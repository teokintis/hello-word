<template>
  <div id="app">
    <h1>Hello World</h1>
    <button @click="fetchMessage">Get Message from Node.js API</button>
    <p v-if="message">{{ message }}</p>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'App',
  data() {
    return {
      message: '',
    };
  },
  methods: {
    async fetchMessage() {
      try {
        const response = await axios.get('http://52.57.9.0:3000/api');
        this.message = response.data.message;
      } catch (error) {
        console.error('There was an error!', error);
      }
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
button {
  margin-top: 20px;
  padding: 10px 20px;
  font-size: 16px;
}
</style>
