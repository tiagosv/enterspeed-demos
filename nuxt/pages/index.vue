<script setup>
import { getByHandle } from "../lib/enterspeed";

const data = await getByHandle("blogList");

const posts = data.blogList.content;
</script>


<template>
  <div class="bg-gray-200">
    <Head>
      <Title>Enterspeed ♥ Nuxt</Title>
    </Head>
    <div
      class="
        px-4
        py-16
        mx-auto
        sm:max-w-xl
        md:max-w-full
        lg:max-w-screen-xl
        md:px-24
        lg:px-8 lg:py-20
      "
    >
      <div
        class="grid gap-8 lg:grid-cols-3 sm:max-w-sm sm:mx-auto lg:max-w-full"
      >
        <a
          v-for="post in posts"
          :key="post.title"
          :href="post.url"
          class="
            overflow-hidden
            transition-shadow
            duration-300
            bg-white
            rounded
            border
            hover:text-blue-800 hover:bg-gray-50
          "
        >
          <img
            :src="post.thumbnail"
            :alt="post.title"
            class="object-cover w-full h-64"
          />
          <div class="p-5">
            <p class="mb-3 text-xs font-semibold tracking-wide uppercase">
              <span class="transition-colors duration-200 text-blue-gray-900">
                {{ post.author.name }}
              </span>
              <span class="text-gray-600"> — {{ post.date }} </span>
            </p>
            <div
              class="
                inline-block
                mb-3
                text-2xl
                font-bold
                leading-5
                transition-colors
                duration-200
              "
            >
              {{ post.title }}
            </div>
            <p class="mb-2 text-gray-700">{{ post.excerpt }}</p>
          </div>
        </a>
      </div>
    </div>
  </div>
</template>