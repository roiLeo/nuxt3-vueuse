<script setup>
// Auto-import with tree-shaking from https://vueuse.org/functions.html#browser
// Thanks to uxt 3 auto import, https://v3.nuxtjs.org/
const { x, y } = useMouse();
const { width, height } = useWindowSize();

const red = computed(() => Math.round((x.value / width.value) * 255));
const green = computed(() => Math.round((y.value / height.value) * 255));
const blue = computed(() => Math.round((red + green) / 2));
const rgb = computed(() => `rgb(${red.value}, ${green.value}, ${y.value})`);
</script>

<template>
  <div class="bg">
    <NuxtWelcome />
  </div>
</template>

<style>
body {
  margin: 0;
  padding: 0;
}
.bg {
  background-color: v-bind(rgb);
  min-height: 100vh;
}
</style>