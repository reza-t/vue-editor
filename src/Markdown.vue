<template>
  <div>
    <div id="markdown">
      <textarea v-model="input" debounce="300"></textarea>
      <div id='compiled' v-html="compiledMarkdown"></div>
    </div>
  </div>
</template>

<script>
import marked from "marked";

export default {
  name: "Markdown",
  data() {
    return {
      input: "# Let's start writing Markdown in vue"
    };
  },

  computed: {
    compiledMarkdown() {
      const compiled =  marked(this.input, { sanitize: true });
      return compiled;
    }
  },
};
</script>

<style>
html,
body,
#markdown {
  margin: 0;
  height: 100%;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen, Ubuntu, Cantarell,
    "Open Sans", "Helvetica Neue", sans-serif;
}

textarea,
#markdown div {
  display: inline-block;
  width: 49%;
  height: 100%;
  vertical-align: top;
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
  padding: 0 20px;
}

textarea {
  border: none;
  border-right: 1px solid #ccc;
  resize: none;
  outline: none;
  background-color: lawngreen;
  font-size: 18px;
  font-family: "Monaco", courier, monospace;
  padding: 20px;
  color: #000000;
}

code {
  color: #f66;
}

#compiled {
  background-color: gray;
}
</style>
