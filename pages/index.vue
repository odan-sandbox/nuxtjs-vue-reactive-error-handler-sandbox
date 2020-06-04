<template>
  <div class="container">
    <button @click="click">
      click me
    </button>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

const sleep = (msec: number) => new Promise(resolve => setTimeout(resolve, msec))
export default Vue.extend({
  mounted () {
    sleep(100).then(() => {
      throw new Error('poypoyo')
    })
  },
  methods: {
    async click () {
      await sleep(100).then(() => {
        throw new Error('poyo')
      })
    }
  }
})
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
