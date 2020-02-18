<template>
  <div>
    <ul>
      <li v-for="post in posts">
        {{ post.fields.name }}
      </li>
    </ul>
  </div>
</template>

<script>
  import client from '~/plugins/contentful.js'

  export default {
    asyncData() {
      return client.getEntries()
        .then(entries => {
          return {
            posts: entries.items
          }
        })
    }
  }
</script>
