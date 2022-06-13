<template>
  <div>
    <v-container>
      <v-flex>
      </v-flex>
      <v-flex>
        <v-flex xs12 pb-3 sm6 offset-sm3 v-for="(article, index) in articles" :key="index">
          <v-card>
            <img :src="article.urlToImage" width="100%" height="200px">

            <v-card-title primary-title>
              <div>
                <div class="headline">{{article.title}}</div>
              </div>
            </v-card-title>
            <v-card-text>Published At: {{article.publishedAt}}</v-card-text>
            <v-card-text>{{article.content}}</v-card-text>
            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn dark :href="article.url" target="_blank">URL</v-btn>
            </v-card-actions>
          </v-card>
        </v-flex>
      </v-flex>
    </v-container>
  </div>
</template>

<script>
export default {
  async asyncData({ app }) {
    const { articles } = await app.$axios.$get(
      "https://newsapi.org/v2/everything?q=tesla&from=2022-05-13&sortBy=publishedAt&apiKey=d94bc71c72f14eca9419bfde30ae72b7"
    );
    return { articles };
  }
};
</script>
