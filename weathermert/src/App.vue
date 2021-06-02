<template>
  <div id="app">
    
     <div class="container">
  <div class="row">
    <div class="col-lg-5">
      <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Weather App"/>
    <h4>"Developed with Mertcan Yiğit"</h4>
    <br>
    <center>
     <select @change="valueHasChanged" class="form-select" style="width: 50%;"  aria-label="Default select example" >
      <option value="denizli">Denizli</option>
      <option value="istanbul">İstanbul</option>
      <option value="adana">Adana</option>
    <option value="adıyaman">Adıyaman</option>
    <option value="afyonkarahisar">Afyonkarahisar</option>
    <option value="ağrı">Ağrı</option>
    <option value="amasya">Amasya</option>
    <option value="ankara">Ankara</option>
    <option value="antalya">Antalya</option>
    <option value="artvin">Artvin</option>
    <option value="aydın">Aydın</option>
    <option value="balıkesir">Balıkesir</option>
    <option value="bilecik">Bilecik</option>
    <option value="bingöl">Bingöl</option>
    <option value="bitlis">Bitlis</option>
    <option value="bolu">Bolu</option>
    <option value="burdur">Burdur</option>
    <option value="bursa">Bursa</option>
    <option value="çanakkale">Çanakkale</option>
    <option value="çankırı">Çankırı</option>
    <option value="çorum">Çorum</option>
    <option value="diyarbakır">Diyarbakır</option>
    <option value="edirne">Edirne</option>
    <option value="elazığ">Elazığ</option>
    <option value="erzincan">Erzincan</option>
    <option value="erzurum">Erzurum</option>
    <option value="eskişehir">Eskişehir</option>
    <option value="gaziantep">Gaziantep</option>
    <option value="giresun">Giresun</option>
    <option value="gümüşhane">Gümüşhane</option>
    <option value="hakkâri">Hakkâri</option>
    <option value="hatay">Hatay</option>
    <option value="ısparta">Isparta</option>
    <option value="mersin">Mersin</option>
    <option value="izmir">İzmir</option>
    <option value="kars">Kars</option>
    <option value="kastamonu">Kastamonu</option>
    <option value="kayseri">Kayseri</option>
    <option value="kırklareli">Kırklareli</option>
    <option value="kırşehir">Kırşehir</option>
    <option value="kocaeli">Kocaeli</option>
    <option value="konya">Konya</option>
    <option value="kütahya">Kütahya</option>
    <option value="malatya">Malatya</option>
    <option value="manisa">Manisa</option>
    <option value="kahramanmaraş">Kahramanmaraş</option>
    <option value="mardin">Mardin</option>
    <option value="muğla">Muğla</option>
    <option value="muş">Muş</option>
    <option value="nevşehir">Nevşehir</option>
    <option value="niğde">Niğde</option>
    <option value="ordu">Ordu</option>
    <option value="rize">Rize</option>
    <option value="sakarya">Sakarya</option>
    <option value="samsun">Samsun</option>
    <option value="siirt">Siirt</option>
    <option value="sinop">Sinop</option>
    <option value="sivas">Sivas</option>
    <option value="tekirdağ">Tekirdağ</option>
    <option value="tokat">Tokat</option>
    <option value="trabzon">Trabzon</option>
    <option value="tunceli">Tunceli</option>
    <option value="şanlıurfa">Şanlıurfa</option>
    <option value="uşak">Uşak</option>
    <option value="van">Van</option>
    <option value="yozgat">Yozgat</option>
    <option value="zonguldak">Zonguldak</option>
    <option value="aksaray">Aksaray</option>
    <option value="bayburt">Bayburt</option>
    <option value="karaman">Karaman</option>
    <option value="kırıkkale">Kırıkkale</option>
    <option value="batman">Batman</option>
    <option value="şırnak">Şırnak</option>
    <option value="bartın">Bartın</option>
    <option value="ardahan">Ardahan</option>
    <option value="ığdır">Iğdır</option>
    <option value="yalova">Yalova</option>
    <option value="karabük">Karabük</option>
    <option value="kilis">Kilis</option>
    <option value="osmaniye">Osmaniye</option>
    <option value="düzce">Düzce</option>
    </select></center>
    </div>
    <div class="col-lg-7">
  <div class="row">
    <center><h2>{{sehir}}</h2></center>
    <br><br>
       <div class="col" v-for="todo in todos" :key="todo">
          <img style="width: 50px;" :src=" todo.icon "> <br>
      {{todo.date}}<br>
        {{todo.day}}<br>
        {{todo.description}}
     
      </div>
       
    </div>
    
    </div>
   
  </div>
</div>
    
  </div>
</template>

<script>
 import axios from 'axios';
import HelloWorld from './components/HelloWorld.vue'
let sehir="Denizli"
let val="istanbul"
let config = {
  headers: {
    "content-type": "application/json",
    "authorization": "yourapi"
  }
}
export default {
  name: 'App',
  components: {
    HelloWorld
  },
  data(){
    return{
       todos: [],
       sehir
    }
  },
  methods: {
    valueHasChanged(e) {
  val = e.target.value;
  console.log(val);
  let buyuk = val.charAt(0).toUpperCase() + val.slice(1);
  this.sehir=buyuk;
   this.created();
   
    },
    async created() {
 
     let res = await axios.get(`https://api.collectapi.com/weather/getWeather?data.lang=tr&data.city=`+val,config);
    console.log(res.data.result);
      this.todos =  res.data.result;
    
  },

  },
   async created() {
 
     let res = await axios.get(`https://api.collectapi.com/weather/getWeather?data.lang=tr&data.city=`+val,config);
    console.log(res.data.result);
      this.todos =  res.data.result;
    
  }, 
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #fff;
  margin-top: 60px;
}
</style>
