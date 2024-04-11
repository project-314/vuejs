<template>
  <li v-for="team in teams">
    <b>{{ team.name }}</b> - <small>{{ team.city }}</small> - {{ team.wins }} / {{ team.losses }}
    <q-btn @click="addScore(true)">Add Win </q-btn>
    <q-btn @click="addScore(false)">Add Loss </q-btn>
  </li>
</template>
<script>
import axios from 'axios'

export default {
  data() {
    return {
      teams: []
    }
  },
  methods:{
    addScore(win){
      axios
      .post('http://localhost:8000/team/', {
        name: 'Magic',
        city: '666',
        wins : 1,
        losses : 2
      })
      .then((response) => console.log(response))
      console.log("5555",win)
    }


  },
  mounted() {
    axios
      .get('http://localhost:8000/teams')
      .then((response) => {
        console.log(response)
        this.teams = response.data
      })
  }
}
</script>
