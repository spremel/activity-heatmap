<template>
<div id="main-div">
  <!-- <b-img id="screen" src="static/heatmap-screen.png" /> -->
  <b-carousel id="screenshots" no-hover-pause>
    <b-carousel-slide img-src="static/screenshots/out-heatmap-cheltenham-dark.png" />
    <b-carousel-slide img-src="static/screenshots/out-heatmap-mallorca-terrain.png" />
    <b-carousel-slide img-src="static/screenshots/out-heatmap-giron-bing.png" />
    <b-carousel-slide img-src="static/screenshots/out-heatmap-britannia-dark.png" />
  </b-carousel>
  <b-button
    id="button-connect"
    size="sm"
    variant="dark"
    v-on:click="loginStrava"
    >
    <b-img src="static/strava-connect.svg" />
  </b-button>
  <b-img id="strava-logo" src="static/strava-logo.svg"/>
</div>
</template>

<script>

import {ORIGIN_SERVER, AUTH_SERVER, CLIENT_ID} from '@/constants.js'
export default {

  name: 'Heatme',
  data () {
    return { }
  },
  methods: {
    loginStrava: () => {
      location.href = `${AUTH_SERVER}/oauth/authorize?client_id=${CLIENT_ID}&response_type=code&redirect_uri=${ORIGIN_SERVER}/token_exchange&approval_prompt=force&scope=activity:read`
    }
  },
  mounted () {
    let olScript = document.createElement('script')
    olScript.setAttribute('src', 'https://cdn.jsdelivr.net/gh/openlayers/openlayers.github.io@master/en/v6.3.1/build/ol.js')
    document.head.appendChild(olScript)
  }
}
</script>

<style scoped>
  #main-div {
    background-color: black;
    width: 100%;
    height: 100%;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
  }
  #button-connect {
    position: absolute;
    top: 95%;
    left: 50%;
    transform: translate(-50%, -50%);
  }
  #screenshots {
    /* position: absolute; */
    margin-top: 50px;
    top: 40%;
    left: 50%;
    transform: translate(-50%, -50%);
  }
  #strava-logo {
    position: absolute;
    top: 90%;
    left: 90%;
  }
</style>
