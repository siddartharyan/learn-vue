<template>
  <Hello :myName="name" />
  <br />
  <input type="text" v-model.trim="name" />
  {{ sum }}
  <button @click="data.push({ amount: 300 })">add</button>
</template>

<script>
import Hello from "./components/Hello";
export default {
  name: "App",
  components: {
    Hello,
  },
  data() {
    return {
      count: 0,
      name: "siddarth",
      data: [{ amount: 100 }, { amount: 200 }],
    };
  },
  methods: {
    add(evnt) {
      console.log(evnt);
      this.count += 1;
    },
    remove() {
      this.count -= 1;
    },
  },
  computed: {
    sum() {
      return this.data.reduce((prev, cur) => prev + cur.amount, 0);
    },
  },
  watch: {
    name(newValue, oldValue) {
      console.log(newValue, oldValue);
    },
    data: {
      handler(newValue) {
        console.log("entered");
      },
      deep: true,
      immediate: true,
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
