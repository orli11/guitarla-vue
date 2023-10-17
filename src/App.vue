<script setup>
import {ref, reactive, onMounted} from 'vue'
import {db} from './data/guitarras'
import Guitarra from './components/Guitarra.vue'
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'

const guitarras = ref([])
const carrito = ref([])

const agregarCarrito = (guitarra) => {
    //console.log(guitarra)
    carrito.value.push(guitarra)
}

onMounted(() => {
   guitarras.value = db
})
</script>

<template>
    <Header 
        :carrito="carrito"
    />
    <main class="container-xl mt-5">
        <h2 class="text-center">Nuestra Colección</h2>
        <div class="row mt-5">
            <Guitarra 
                v-for="guitarra in guitarras"
                v-bind:guitarra="guitarra"
                @agregar-carrito="agregarCarrito"
             />
        </div>
    </main>
    <Footer />
</template>

<style>
</style>