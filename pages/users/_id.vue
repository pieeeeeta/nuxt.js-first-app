<template>
  <section class="container">
    <div>
    </div>
  </section>
</template>

<script>
  export default {
    head() {
      return {
        title: this.user.id
      }
    },
    async asyncData({route, app}) {
      const user = await app.$axios.$get(`https://qiita.com/api/v2/users/${route.params.id}`)
      const items = 
        await app.$axios.$get(`https://qiita.com/api/v2/items?query=user:${route.params.id}`)
      return { user, items }

    }
  }

</script>