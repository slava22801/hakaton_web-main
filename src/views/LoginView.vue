<template>
    <div class="about">
      <el-menu class="nav" :default-active="activeIndex" router mode="horizontal">
      <el-menu-item index="1" route="/admin/providers">Поставщики</el-menu-item>
      <el-menu-item index="2" route="/admin/menu">Список товаров</el-menu-item>
      
      </el-menu>
      <h1>Авторизация</h1>
      <el-input v-model="authInput.txtEmail" class="w3-margin" placeholder="Email"></el-input>
      <el-input v-model="authInput.txtPassword" class="w3-margin" placeholder="Пароль" type="password"></el-input>
      <el-button @click="signIn()" type="success">Войти</el-button>
      <el-button @click="signUp()" type="warning">Зарегистрироваться</el-button>
      <hr>
      {{ user }}
    </div>
</template>
<script>
import {store} from '../store'
export default{
  data(){
    return{
      authInput: {
                    txtEmail: '',
                    txtPassword: ''
                }
    }
  },
  computed:{
    user(){ return store.state.user }
  },
  methods:{
    signIn(){
      store.dispatch('signIn', { email:this.authInput.txtEmail, password:this.authInput.txtPassword })
    }
  }
}

</script>
<style>
   .about{

     text-align: center;
     width: 50%;
     margin: auto;
   }
</style>