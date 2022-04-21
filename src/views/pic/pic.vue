<template>
  <div class="masonry">
    <div class="item" :key="i.id" v-for="i in data">
      <img :src="i.img" />
      <span class="title"> {{ i.value }}</span>
    </div>
  </div>
</template>

<script setup>
import faker from "@faker-js/faker";
const data = [];
const getImg = () => {
  if (Math.random() > 0.5) {
    return "https://fakeimg.pl/250x180";
  }
  return "https://fakeimg.pl/350x200";
};
for (let index = 0; index < 10; index++) {
  data.push({
    id: index,
    value: faker.random.words(15),
    img: getImg(),
  });
}
console.log(data);
</script>

<style lang="scss" scoped>
.masonry {
  column-count: 3;
  column-gap: 10px;
  padding: 10px;
  .item {
    break-inside: avoid;
    border: 1px solid #999;
    margin-bottom: 10px;
    img {
      width: 100%;
      vertical-align: middle;
    }
    .title {
      display: block;
      margin-left: 5px;
    }
  }
}
</style>
