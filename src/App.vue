<template>
  <div id="app">
    <vue-query-builder :rules="rules" v-model="query"></vue-query-builder>

    <p>Generated output:</p>

    <pre>{{ JSON.stringify(this.query, null, 2) }}</pre>
  </div>
</template>

<script>
import VueQueryBuilder from "vue-query-builder";
import VueSlideBar from "vue-slide-bar";

export default {
  name: "App",
  components: { VueQueryBuilder },

  data() {
    return {
      rules: [
        {
          type: "custom-component",
          id: "percentage",
          label: "Percentage",
          operators: ["="],
          component: VueSlideBar,
          default: 50
        }
      ],

      query: {
        logicalOperator: "any",
        children: [
          {
            type: "query-builder-rule",
            query: {
              rule: "percentage",
              operator: "=",
              operand: "Percentage",
              value: 55
            }
          }
        ]
      }
    };
  }
};
</script>
<style>
.vqb-custom-component-wrap {
  flex-grow: 1;
  padding-right: 15px;
}
</style>