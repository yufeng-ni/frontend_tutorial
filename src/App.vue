<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import axios from 'axios'
import { reactive } from 'vue'


const bd = reactive({
  name: 'jonathan',
  age: 33,
  orders: [
    { orderNumber: 1, qty: 11 },
    { orderNumber: 2, qty: 22 },
    { orderNumber: 3, qty: 33 },
    { orderNumber: 4, qty: 44 },
    { orderNumber: 5, qty: 55 },
  ]
})


async function fetchSomething () {
  //#region get请求
  // axios.get('https://jsonplaceholder.typicode.com/todos/1').then(res => {
  //   console.log(res)
  // })

  // axios.get('/sap/opu/odata/sap/zh5_app_srv/').then(res => {
  //   console.log(res)
  // })
  //#endregion get请求


  //#region post 请求
  // const data = {
  //   "Username": "asdf",
  //   "NfcTag": "",
  //   "WmMovement": true,
  //   "ImMovement": false,
  //   "to_ltak": { "Lgnum": "333" },
  //   "to_ltap": [{ "Lgnum": "333" }],
  //   "to_mkpf": { "Mblnr": "xxxxx" },
  //   "to_mseg": [{ "Mblnr": "xxxxx" }],
  //   "to_bapiret2": []
  // }

  // const token = await axios.get('/sap/opu/odata/sap/zh5_app_srv/', { headers: { 'x-csrf-token': 'Fetch' } }).then(response => {
  //   return response.headers['x-csrf-token']
  // })
  // let headers = {
  //   'x-csrf-token': token
  // }
  // axios.post('/sap/opu/odata/sap/zh5_app_srv/GoodsMovement', data, { headers: headers }).then(res => {
  //   console.log(res.data)
  // })
  //#endregion post 请求
}
function showSomething () {
  console.log('showSomething')
}
</script>

<template>
  <!-- <nav> -->
  <!-- <RouterLink to="/">Home</RouterLink> -->
  <!-- <RouterLink to="/about">About</RouterLink> -->
  <!-- </nav> -->
  <!-- <RouterView /> -->

  <!-- 调用网络请求 -->
  <button @click="fetchSomething()">我是按钮</button>
  <br>

  <!-- 单向绑定 -->
  {{ bd.name }}
  <input type="text" v-bind:value="bd.name">
  <input type="text" :value="bd.name">

  <!-- 双向绑定 -->
  <br>
  {{ bd.age }}
  <input type="number" v-model="bd.age">

  <!-- v-if -->
  <div v-if="bd.age < 40">
    我是v-if的例子
  </div>

  <!-- disable -->
  <div>
    <button :disabled="bd.age > 40" @click="showSomething()">我是disable的例子</button>
  </div>

  <!-- v-for -->
  <div v-for="(item, index) in 12" :key="index" style="border: solid 1px red">
    {{ item }}
  </div>

  <div v-for="(item, index) in bd.orders" :key="index" style="border: solid 1px green">
    {{ `订单行项目: ${item.orderNumber}, 订单数量: ${item.qty}` }}
  </div>

</template>
