<script>
export default {};
</script>

<style></style>

<script>
export default {};
</script>

<style></style>

<template>
  <div>
    <div
      class="card"
      :style="`background-color:${item.background};`"
      :class="item.class"
    >
      <a
        :href="item.url"
        class="linkoverlay"
        :target="item.target"
        rel="noreferrer"
      ></a>
      <div class="card-content">
        <div class="media">
          <div v-if="item.logo" class="media-left">
            <figure class="image is-48x48">
              <img :src="item.logo" :alt="`${item.name} logo`" />
            </figure>
          </div>
          <div v-if="item.icon" class="media-left">
            <figure class="image is-48x48">
              <i class="thirty-five" :class="['fa-fw', item.icon]"></i>
            </figure>
          </div>
          <div class="media-content">
            <p class="title is-4">{{ item.name }}</p>
            <p class="subtitle is-6">{{ item.subtitle }}</p>
          </div>
        </div>
        <a
          v-if="item.info"
          :href="item.info"
          :target="item.infotarget"
          rel="noreferrer"
        >
          <div class="infolink">
            <i class="fas fa-info-circle"></i>
          </div>
        </a>
        <div
          v-on:click="filterTag()"
          class="tag is-clickable"
          :class="item.tagstyle"
          v-if="item.tag"
        >
          <strong class="tag-text">#{{ item.tag }}</strong>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Generic",
  props: {
    item: Object,
  },
  methods: {
    filterTag: function () {
      this.$emit("filter", this.item.tag.toLowerCase());
    },
  },
};
</script>

<style scoped lang="scss">
.media-left img {
  max-height: 100%;
}
</style>
