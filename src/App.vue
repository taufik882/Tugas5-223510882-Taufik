<template>
  <q-layout view="hHh LpR fFf">
    <q-header elevated class="header">
      <q-toolbar>
        <q-avatar>
          <img src="./assets/icon.jpeg">
        </q-avatar>
        <q-toolbar-title>Taufik Shop</q-toolbar-title>
        <q-btn flat round dense icon="shopping_cart" />
      </q-toolbar>
      <q-tabs v-model="tab">
        <q-btn flat label="Pakaian" @click="scrollToSection('pakaian-section')" />
        <q-btn flat label="Celana" @click="scrollToSection('celana-section')" />
        <q-btn flat label="Sepatu" @click="scrollToSection('sepatu-section')" />
      </q-tabs>
    </q-header>

    <q-page-container>
      <div class="q-pa-md">
        <q-carousel
          animated
          v-model="slide"
          infinite
          :autoplay="autoplay"
          arrows
          transition-prev="slide-right"
          transition-next="slide-left"
          @mouseenter="autoplay = false"
          @mouseleave="autoplay = true"
        >
          <q-carousel-slide :name="'promo1'" :img-src="getImage('promo1.jpeg')" style="height: 100%;" />
          <q-carousel-slide :name="'promo2'" :img-src="getImage('promo2.jpg')" style="height: 100%;" />
          <q-carousel-slide :name="'promo3'" :img-src="getImage('promo3.jpg')" style="height: 100%;" />
          <q-carousel-slide :name="'promo4'" :img-src="getImage('promo4.jpg')" style="height: 100%;" />
        </q-carousel>

        <div id="pakaian-section" class="q-mt-xl section">
          <h3 class="section-title">Pakaian</h3>
          <div class="q-gutter-md q-mt-lg row justify-center">
            <q-card v-for="(product, index) in pakaianProducts" :key="'pakaian-' + index" class="my-card">
              <q-carousel animated arrows infinite v-model="productSlides['pakaian-' + index]">
                <q-carousel-slide v-for="img in product.images" :name="img.name" :img-src="img.src" :key="img.name" />
              </q-carousel>
              <q-card-section>
                <div class="text-h6">{{ product.name }}</div>
                <div class="text-subtitle2">Harga: {{ product.price }}</div>
              </q-card-section>
              <q-card-actions align="right">
                <q-btn flat label="Detail" color="primary" @click="showDetail(product.description)" />
              </q-card-actions>
            </q-card>
          </div>
        </div>

        <div id="celana-section" class="q-mt-xl section">
          <h3 class="section-title">Celana</h3>
          <div class="q-gutter-md q-mt-lg row justify-center">
            <q-card v-for="(product, index) in celanaProducts" :key="'celana-' + index" class="my-card">
              <q-carousel animated arrows infinite v-model="productSlides['celana-' + index]">
                <q-carousel-slide v-for="img in product.images" :name="img.name" :img-src="img.src" :key="img.name" />
              </q-carousel>
              <q-card-section>
                <div class="text-h6">{{ product.name }}</div>
                <div class="text-subtitle2">Harga: {{ product.price }}</div>
              </q-card-section>
              <q-card-actions align="right">
                <q-btn flat label="Detail" color="primary" @click="showDetail(product.description)" />
              </q-card-actions>
            </q-card>
          </div>
        </div>

        <div id="sepatu-section" class="q-mt-xl section">
          <h3 class="section-title">Sepatu</h3>
          <div class="q-gutter-md q-mt-lg row justify-center">
            <q-card v-for="(product, index) in sepatuProducts" :key="'sepatu-' + index" class="my-card">
              <q-carousel animated arrows infinite v-model="productSlides['sepatu-' + index]">
                <q-carousel-slide v-for="img in product.images" :name="img.name" :img-src="img.src" :key="img.name" />
              </q-carousel>
              <q-card-section>
                <div class="text-h6">{{ product.name }}</div>
                <div class="text-subtitle2">Harga: {{ product.price }}</div>
              </q-card-section>
              <q-card-actions align="right">
                <q-btn flat label="Detail" color="primary" @click="showDetail(product.description)" />
              </q-card-actions>
            </q-card>
          </div>
        </div>
      </div>
    </q-page-container>

    <q-footer reveal elevated class="footer">
      <q-toolbar>
        <q-toolbar-title class="footer-title">
          <div class="footer-content">
            <div>Created by Taufik Mahaldi</div>
            <div>&copy; 2024 Taufik Shop. All rights reserved.</div>
          </div>
        </q-toolbar-title>
      </q-toolbar>
    </q-footer>
  </q-layout>
</template>

<script setup>
import { ref } from 'vue'

const slide = ref('promo1')
const autoplay = ref(true)
const tab = ref('pakaian')

const productSlides = ref({
  'pakaian-0': 'first',
  'pakaian-1': 'first',
  'pakaian-2': 'first',
  'pakaian-3': 'first',
  'pakaian-4': 'first',
  'celana-0': 'first',
  'celana-1': 'first',
  'celana-2': 'first',
  'celana-3': 'first',
  'celana-4': 'first',
  'sepatu-0': 'first',
  'sepatu-1': 'first',
  'sepatu-2': 'first',
  'sepatu-3': 'first',
  'sepatu-4': 'first',
})

const pakaianProducts = [
  {
    name: 'Erigo T-Shirt Project Summer Black',
    price: 'Rp 200.000',
    description: "T-shirt yang cocok untuk dipadukan dengan berbagai jenis celana",
    images: [
      { name: 'first', src: getImage('erigo1.jpg') },
      { name: 'second', src: getImage('erigo2.jpg') },
      { name: 'third', src: getImage('erigo3.jpg') },
   
    ]
  },
  {
    name: 'Workout Streetwear x Scribbles Kaos Tshirt Distro Bubblecity',
    price: 'Rp 150.000',
    description: 'T-shirt yang cocok untuk dipadukan dengan berbagai jenis celana',
    images: [
      { name: 'first', src: getImage('tsh21.jpg') },
      { name: 'second', src: getImage('tsh22.jpg') },
      { name: 'third', src: getImage('tsh23.jpg') },
    ]
  },
  {
    name: 'Insurgent Club - Heavyweight Tshirt Kaos Human Not Humanity Black',
    price: 'Rp 250.000',
    description: 'T-shirt dengan kualitas terbaik, kami menggunakan Tinta Plastisol untuk detail sablon. Tinta ini menjadi pilihan terbaik karena memiliki kualitas warna sablon terbaik, warna terlihat cerah dan tidak kusam.',
    images: [
      { name: 'first', src: getImage('tsh31.jpg') },
      { name: 'second', src: getImage('tsh32.jpg') },
      { name: 'third', src: getImage('tsh33.jpg') },
    ]
  },
  {
    name: 'Insurgent Club - Tshirt Kaos Mind Explosion Black',
    price: 'Rp 300.000',
    description: 'T-shirt dengan kualitas terbaik, kami menggunakan Tinta Plastisol untuk detail sablon. Tinta ini menjadi pilihan terbaik karena memiliki kualitas warna sablon terbaik, warna terlihat cerah dan tidak kusam.',
    images: [
      { name: 'first', src: getImage('tsh41.jpg') },
      { name: 'second', src: getImage('tsh42.jpg') },
      { name: 'third', src: getImage('tsh43.jpg') },
    ]
  },
]

const celanaProducts = [
  {
    name: 'AlfheimCloth.Inc - Celana Jeans Pria Long Pants Denim - Slim Fit Pria GreyWashing Denim',
    price: 'Rp 300.000',
    description: 'ALFHEIM CLOTH.Inc Long Pants Denim dengan Bahan BADJATEX adalah salah satu Celana Denim terbaik dan berkualitas tinggi di antara Local Brand Indonesia. Dibuat dengan Bahan BADJATEX Denim strech dengan bahan terbaik sehingga menjadikan Celana Denim yang Tebal, Lembut, dan Nyaman untuk digunakan dalam kegiatan sehari-hari. Dapatkan long lasting tee dengan warna terbaik untuk merasa muda selamanya ! ',
    images: [
      { name: 'first', src: getImage('cln11.jpg') },
      { name: 'second', src: getImage('cln12.jpg') },
      { name: 'third', src: getImage('cln13.jpg') },
    ]
  },
  {
    name: 'AlfheimCloth.Inc Colby Scratch Celana Panjang Denim - Slim Fit Longpants Denim',
    price: 'Rp 280.000',
    description: 'ALFHEIM CLOTH.Inc Long Pants Denim adalah salah satu Celana Denim terbaik dan berkualitas tinggi di antara Local Brand Indonesia. Dibuat dengan bahan Denim strech dengan bahan terbaik sehingga menjadikan Celana Denim yang Tebal, Lembut, dan Nyaman untuk digunakan dalam kegiatan sehari-hari. Dapatkan long lasting tee dengan warna terbaik untuk merasa muda selamanya ! ',
    images: [
      { name: 'first', src: getImage('cln21.jpg') },
      { name: 'second', src: getImage('cln22.jpg') },
      { name: 'third', src: getImage('cln23.jpg') },
    ]
  },
  {
    name: 'Celana Surfing PS High Quality DS4601',
    price: 'Rp 350.000',
    description: 'Accesories Lengkap/Full Hand Tag, Bahan Sangat Berkualitas Di Jamin Adem Dan Nyaman di pakai ,jahitan Rapih, warna tidak mudah pudar, Denim strech',
    images: [
      { name: 'first', src: getImage('cln31.jpg') },
      { name: 'second', src: getImage('cln32.jpg') },
      { name: 'third', src: getImage('cln33.jpg') },
    ]
  },
  {
    name: 'Celana Surfing PS High Quality DS5157',
    price: 'Rp 380.000',
    description: 'Accesories Lengkap/Full Hand Tag, Bahan Sangat Berkualitas Di Jamin Adem Dan Nyaman di pakai ,jahitan Rapih, warna tidak mudah pudar, Denim strech',
    images: [
      { name: 'first', src: getImage('cln41.jpg') },
      { name: 'second', src: getImage('cln42.jpg') },
      { name: 'third', src: getImage('cln43.jpg') },
    ]
  },
]

const sepatuProducts = [
  {
    name: 'MOERELLI &CO White Gray Sepatu Sneakers Pria Sabeza Mr6130 Putih Men Shoes',
    price: 'Rp 500.000',
    description: `Shoes Material:
Upper      : Javana Premium Leather Syntethic
Lining     : Jersy 
Out Sole   : Microtex Tpr
Insole     : UltraSoft Foam 3.0`,
    images: [
      { name: 'first', src: getImage('spt11.jpg') },
      { name: 'second', src: getImage('spt12.jpg') },
      { name: 'third', src: getImage('spt13.jpg') },
    ]
  },
  {
    name: 'Moerelli &Co Silvano Putih Sepatu Pria Sneakers Full White Mr 6105 Sol List Brown',
    price: 'Rp 450.000',
    description: `Shoes Material:
Upper      : Javana Premium Leather Syntethic
Lining     : Jersy 
Out Sole   : Microtex Tpr
Insole     : UltraSoft Foam 3.0`,
    images: [
      { name: 'first', src: getImage('spt21.jpg') },
      { name: 'second', src: getImage('spt22.jpg') },
      { name: 'third', src: getImage('spt23.jpg') },
    ]
  },
  {
    name: 'DEVANO BLACK |ManNeedMe x NAZ| Sepatu Sneakers Pria Casual Shoes JAHIT SOL PREMIUM',
    price: 'Rp 400.000',
    description: 'Devano dirancang dengan desain dan perpaduan warna yang Elegan, membuatnya tampak casual dan juga sporty. Dibagian dalam berlapis spon dan mesh yang membuat nyaman dipakai. Ditambah dengan sol yang ringan tapi juga kuat + anti slip, cocok dipakai untuk berbagai aktivitas dengan tetap memperhatikan penampilan penggunanya.',
    images: [
      { name: 'first', src: getImage('spt31.jpg') },
      { name: 'second', src: getImage('spt32.jpg') },
      { name: 'third', src: getImage('spt33.jpg') },
    ]
  },
  {
    name: 'RANGER WHITE |ManNeedMe x NAZ| Sepatu Sneakers Wanita / Pria Casual Shoes Unisex JAHIT SOL PREMIUM',
    price: 'Rp 480.000',
    description: 'Ranger dirancang dengan desain dan perpaduan warna yang Elegan, membuatnya tampak casual dan juga sporty. Dibagian dalam berlapis spon dan mesh yang membuat nyaman dipakai. Ditambah dengan sol yang ringan tapi juga kuat + anti slip, cocok dipakai untuk berbagai aktivitas dengan tetap memperhatikan penampilan penggunanya.',
    images: [
      { name: 'first', src: getImage('spt41.jpg') },
      { name: 'second', src: getImage('spt42.jpg') },
      { name: 'third', src: getImage('spt43.jpg') },
    ]
  },
]

function getImage(imageName) {
  const url = new URL(`./assets/${imageName}`, import.meta.url).href
  return url;
}

function scrollToSection(sectionId) {
  const section = document.getElementById(sectionId)
  if (section) {
    section.scrollIntoView({ behavior: 'smooth' })
  }
}

function showDetail(description) {
  alert(description)
}
</script>

<style scoped>
.header {
  background-color: #1976D2;
  color: white;
}

.section {
  background-color: #FAFAFA;
  padding: 2rem;
  border-radius: 0.5rem;
  margin-bottom: 2rem;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.section-title {
  font-size: 1.5rem;
  color: #333;
  text-align: center;
  margin-bottom: 1rem;
}

.my-card {
  width: 100%;
  max-width: 300px;
  border-radius: 0.5rem;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  margin-bottom: 1.5rem;
}

.q-card-section {
  padding: 1rem;
}

.q-card-section .text-h6 {
  font-size: 1.2rem;
  color: #333;
}

.q-card-section .text-subtitle2 {
  font-size: 1rem;
  color: #555;
}

.footer {
  background-color: #1976D2;
  color: white;
  text-align: center;
  padding: 1rem 0;
}

.footer-title {
  text-align: center;
  width: 100%;
}

.footer-content {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
