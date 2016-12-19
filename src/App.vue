<template>
  <div id="app">
    <async-content :map-function="mapFunction" url="http://www.codeofmanycolors.com/blog/wp-json/wp/v2/posts?per_page=1">
      <div>
        <h3>{{{posts[0].title}}}</h3>
        <div>
          {{{posts[0].excerpt}}}
        </div>
      </div>
    </async-content>
  </div>
</template>
<script>
import asyncContent from './async-content.vue'
export default {
  components: {
    asyncContent
  },
  data: function () {
    const vm = {
      posts: [],
      mapFunction: (json)=> {
        vm.posts = json.map (p=> {
          return {
            title: p.title.rendered,
            excerpt: p.excerpt.rendered
          }
        })
      }
    }
    return vm
  }
}
</script>

<style>
  body {
    font-family: Helvetica, sans-serif;
  }
  
</style>