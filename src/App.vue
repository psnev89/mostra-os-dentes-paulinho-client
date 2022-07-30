<script setup>
import {ref} from "vue";
import axios from "axios";
const res = ref(null);
const sUrl = import.meta.env.DEV ? "http://localhost:5000" : "https://mostra-os-dentes-paulinho-server-eoevgk453-psnev89.vercel.app";
const axiosConfig = {
  headers: {
    'X-Requested-With': 'XMLHttpRequest',
    'Access-Control-Allow-Origin': '*',
    'Content-Type': 'application/json',
  },
};

axios.get(`${sUrl}`, axiosConfig)
.then(({data}) => {
  res.value = data;
}).catch((e) => {
  res.value = e;
})
</script>

<template>
  <div>
    <h1>Mostra os dentes, Paulinho</h1>
    <pre>
      {{ res }}
    </pre>
  </div>
</template>

<style scoped>
h1 {
  text-align: center;
}

pre {
  padding: 10px;
  font-size: 12px;
  line-height: 12px;
}
</style>
