<template>
    <div>
        <h1>IMDB movies:</h1>
        <div class="nav">
            <button>Lowest rated</button>
            <button>Highest rated</button>
        </div>
        <ul>
            <li v-for="(movie, index) in movies" :key="index">
                {{ movie.Title }} <span>Movie rating</span>
            </li>
        </ul>
    </div>
</template>

<script>
  export default {
    name: 'Movie',
    props: {
      msg: String
    },
    data() {
      return {
        movies: []
      }
    },
    mounted() {
      this.getMovies();
    },
    methods: {
      getMovies() {
        let self = this
        fetch('http://omdbapi.com/?s=fast&apikey=17ca5865&plot=full').then(function (response) {
          return response.json()
        }).then(function (result) {
          self.movies = result.Search.slice(0, 15)
          // well, I cant get the movie rating
        })
      }
    }
  }
</script>

<style scoped>
</style>
