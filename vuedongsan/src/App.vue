<template>

  <Modal/>
  <Discount/>




  <div class="menu">
    <a v-for="(a,i) in 메뉴들" :key="i">{{ a }}</a>
  </div>
  
  <div v-for="(원룸,i) in 원룸들" :key="i">
    <img :src="원룸.image" class="room-img">
    <h4 @click="모달창열렸니 = true; 누른거 = i">{{원룸.title}}</h4>
    <p>{{원룸.price}}</p>
  </div>

</template>

<script>

import data from './assets/oneroom.js';
import Discount from './Discount.vue';
import Modal from './assets/Modal.vue';

export default {
  name: 'App',
  // 데이터 보관함
  data(){
    return {
      누른거 : 0,
      원룸들 : data,
      모달창열렸니 : false,
      메뉴들 : ['Home','Shop','About'],
    }
  },
  methods : {
    increase(){
      this.신고수 += 1;
    },
    getSrc(index){
      return require('./assets/room'+index+'.jpg');
    }

  },
  components: {
    Discount // Discount : Discount
    ,
    Modal
}
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu {
  background : darkslateblue;
  padding : 15px;
  border-radius : 5px;
}
.menu a {
  color : white;
  padding : 10px;
}
.room-img {
  width: 100%;
  margin-top: 40px;
}

body {
  margin : 0;
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%; height:100%;
  background: rgba(0,0,0,0.5);
  position: fixed; padding: 20px;
}
.white-bg {
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
} 
.discount {
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}
</style>
