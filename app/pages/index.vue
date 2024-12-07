<template>
  <div>
    <div v-for="post in posts" :key="post._path">
      <a :href="post._path">{{ post.title }}</a>
    </div>
  </div>
</template>

<script setup>
const {data: posts} = await useAsyncData('posts', () =>
    queryContent('/posts')
        .sort({title: 1})
        .find()
)
</script>