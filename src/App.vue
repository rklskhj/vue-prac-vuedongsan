<template>
  <div class="black-bg" v-if="modal === true">
    <div
      class="white-bg"
      v-for="(b, i) in onerooms.filter((oneroom) => oneroom.id === oneroomid)"
      :key="i"
    >
      <a class="X" @click="modal = false">X</a>
      <h4>{{ b.title }}</h4>
      <p>{{ b.content }}</p>
    </div>
  </div>

  <div class="menu">
    <a v-for="a in menus" :key="a">{{ a }}</a>
  </div>
  <div v-for="(b, i) in onerooms" :key="i">
    <img class="image" :src="onerooms[i].image" />
    <h4 @click="handlermodal(i)">{{ onerooms[i].title }}</h4>
    <p>{{ onerooms[i].content }}</p>
    <p>{{ onerooms[i].price }}원</p>
  </div>
</template>

<script>
import data from "./assets/post";

export default {
  name: "App",
  data() {
    return {
      oneroomid: 0,
      onerooms: data,
      modal: false,
      count: [0, 0, 0],
      menus: ["Home", "Shop", "About"],
      price: ["30만원", "50만원", "70만원"],
      products: ["역삼동원룸", "천호동원룸", "마포구원룸"],
    };
  },
  methods: {
    handlermodal(i) {
      this.modal = true;
      this.oneroomid = i;
      console.log("====>", this.oneroomid);
    },
  },
  components: {},
};
</script>

<style>
body {
  margin: 0;
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}
.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 10px;
  cursor: pointer;
}
.image {
  margin-top: 40px;
  width: 100%;
  height: 20em;
}
.X {
  cursor: pointer;
  display: flex;
  justify-content: flex-end;
  margin-top: -5px;
  margin-bottom: -30px;
}
</style>
