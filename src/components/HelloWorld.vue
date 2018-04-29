<template>
  <div class="hello">
    <input @keypress.enter="search" v-model="q">
    <button @click="search">Search</button>
    <div v-for="movie in movies" :key="movie.imdbID">
      <h1>{{movie.Title}}</h1>
      <img :src="movie.Poster" alt="">
    </div>
  </div>
</template>

<script>
// import axios from 'axios'
import {mapActions, mapGetters} from 'vuex'
export default {
  name: 'HelloWorld',
  data () {
    return {
      q: 'avenger'
      // movies: []
    }
  },
  async created () {
    // let movies = await axios.get('http://www.omdbapi.com/?s=avenger&apikey=409a3997')
    // this.movies = movies.data.Search
    this.fetchMovies(this.q)
  },
  computed: {
    ...mapGetters(['movies'])
  },
  methods: {
  // async search (){
  // let movies = await axios.get('http://www.omdbapi.com/?s='+this.q+'&apikey=409a3997')
  // this.movies = movies.data.Search
    ...mapActions(['fetchMovies']),
    search () {
      this.fetchMovies(this.q)
    }
  }
}
</script>
