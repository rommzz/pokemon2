<template>
  <div v-if="!loading" class="row justify-content-center">
    <div v-for="(item, index) in list.results" :key="index" class="card col-12 col-md-3 m-2" style="width: 18rem;">
      <img alt="images">
      <div class="card-body">
        <h5 class="card-title">{{item.name}}</h5>
        <a href="#" class="btn btn-primary">Check Details</a>
      </div>
    </div>
  </div>
  <div v-else class="text-center">
    <div class="spinner-border" role="status">
      <span class="sr-only">Loading...</span>
    </div>
  </div>
</template>
<script>
export default {
  data () {
    return {
      list: [],
      loading: false
    }
  },
  created () {
    this.getPokemonList()
  },
  methods: {
    async getPokemonList () {
      this.loading = true
      this.list = await this.$axios.$get('/pokemon')
      console.log('list pokemon', this.list)
      this.loading = false
    }
  }
}
</script>
