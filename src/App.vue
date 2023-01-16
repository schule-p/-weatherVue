<template>
  <div class="wrapper">
    <input type="text" v-model="city" placeholder="город" @change="getWeather()">
    <p v-if="info != null">{{ info }}°</p>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data(){
    return{
      city:"",
      info: null,
      hueColor:100
    }
  },
  methods:{
    getWeather(){
      if(this.city === "" || this.city.trim().length < 2){
        return false
      }
      axios.get(`https://api.openweathermap.org/data/2.5/weather?q=${this.city}&units=metric&appid=3d9de74844d28377e81415151cbe6a66`)
        .then(res => (this.info = Math.round(res.data.main.temp)))
        
       
    }
  }
};
</script>

<style>

.wrapper{
  width: 500px;
  height: 500px;
  border-radius: 250px;
  background-color: #c38d9d;
  text-align: center;
  text-justify: center;
  align-content: center;
  color: white ;
  vertical-align: middle;
  display: table-cell;

  font-family: "Roboto";

}
.wrapper input{
  width: 250px;
  height: 60px;
  font-size: 35px;
  border-radius: 30px;
  padding: 5px;
  color: rgb(255, 255, 255) ;
  font-family: "Roboto";
  text-align: center;
  Border: none; 
  outline: none;
  background-color: #85cdca;
}

.wrapper input::placeholder{
  color: rgba(255, 255, 255, 0.767);
}

.wrapper p{
  font-size: 250px
}

</style>
