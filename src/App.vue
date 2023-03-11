<script setup>
import { ref, computed } from "vue";

const msg = "contador con vue 3";

const handleClick = (msg) => {
  console.log(msg);
};

const counter = ref(0);

const arrayFavoritos = ref([]);

const increment = () => counter.value++;

const decrement = () => counter.value--;

const reset = () => (counter.value = 0);

const add = () => {
  arrayFavoritos.value.push(counter.value);
};

const blockbtnadd = computed(() => {
  const numSearch = arrayFavoritos.value.find((num) => num === counter.value);
  console.log(numSearch);
  return numSearch || numSearch === 0;
});

const classCounted = computed(() => {
  if (counter.value === 0) {
    return "zero";
  }
  if (counter.value > 0) {
    return "positive";
  }
  if (counter.value < 0) {
    return "negative";
  }
});
</script>

<template>
  <div class="container text-center mt-3">
    <h1>Hola {{ msg.toUpperCase() }}</h1>
    <h2 :class="classCounted">{{ counter }}</h2>
    <div class="btn-group">
      <button @click="increment" class="btn btn-success">Aumentar</button>
      <button @click="decrement" class="btn btn-danger">Disminuir</button>
      <button @click="reset" class="btn btn-secondary">Resetear</button>
      <button @click="add" :disabled="blockbtnadd" class="btn btn-primary">
        Add
      </button>
    </div>
    <ul class="list-group mt-4">
      <li
        v-for="(num, index) in arrayFavoritos"
        :key="index"
        class="list-group-item"
      >
        {{ num }}
      </li>
    </ul>
  </div>
</template>

<style scoped>
h1 {
  color: brown;
  font-weight: bold;
}
.positive {
  color: green;
  font-weight: bolder;
}
.negative {
  color: red;
  font-weight: bolder;
}
.zero {
  color: black;
  font-weight: bolder;
}
</style>
