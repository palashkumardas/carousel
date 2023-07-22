<script setup>
import { ref,reactive } from 'vue';

// Sample images, replace with your own images or load them dynamically as needed
const images = [

  'https://images.unsplash.com/photo-1682685797769-481b48222adf?ixlib=rb-4.0.3&ixid=M3wxMjA3fDF8MHxlZGl0b3JpYWwtZmVlZHwxfHx8ZW58MHx8fHx8&auto=format&fit=crop&w=300&q=60',
  'https://images.unsplash.com/photo-1682695794816-7b9da18ed470?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDZ8fHxlbnwwfHx8fHw%3D&auto=format&fit=crop&w=300&q=60',
  'https://images.unsplash.com/photo-1682685797661-9e0c87f59c60?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE4fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=300&q=60',
  'https://plus.unsplash.com/premium_photo-1666963323736-5ee1c16ef19d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE2fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=300&q=60'
  // Add more image URLs here
];

const currentIndex = ref(0);

const currentImage = ref(images[currentIndex.value]);

const nextImage = () => {
  if (currentIndex.value < images.length - 1) {
    currentIndex.value++;
    currentImage.value = images[currentIndex.value];
  }
};

const previousImage = () => {
  if (currentIndex.value > 0) {
    currentIndex.value--;
    currentImage.value = images[currentIndex.value];
  }
};
</script>


<template>
    <div class="image-carousel">
        <button @click="previousImage" :disabled="currentIndex === 0">Previous</button>
        <img :src="currentImage" alt="Carousel Image" />
        <button @click="nextImage" :disabled="currentIndex === images.length - 1">Next</button>
  </div>
</template>

<style scoped>
/* Add your custom styles here */
.image-carousel {
  display: flex;
  justify-content: center;
  align-items: center;
  max-width: 600px;
  margin: 0 auto;
}

button {
  margin: 10px;
}
</style>