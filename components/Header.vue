<template>
  <header
    id="header"
    class="border-bottom"
  >
    <div class="p-4 row align-items-center justify-content-between">
      <router-link
        to="/"
        class="text-decoration-none col-md-12 col-lg-9"
      >
        <h2 class="mx-3 font-dancing">
          {{ $site.title }}
        </h2>
      </router-link>
      <SearchBox class="col-md-12 col-lg-3 mt-4 d-flex justify-content-end" />
    </div>
    <nav class="px-5">
      <el-menu
        v-if="$themeConfig.nav"
        :default-active="activeIndex"
        mode="horizontal"
        class="d-flex justify-content-center border-0"
      >
        <el-menu-item
          v-for="(item, index) in $themeConfig.nav"
          :index="index.toString()"
          :key="item.text"
          @click="$router.push(item.link)"
        >
          <router-link
            :to="item.link"
            class="text-decoration-none d-block h-100 w-100"
          >
            <i
              v-if="item.icon"
              :class="item.icon"
            ></i>
            {{ item.text }}
          </router-link>
        </el-menu-item>
      </el-menu>
    </nav>
  </header>
</template>

<script>
import SearchBox from "./SearchBox";

export default {
  components: { SearchBox },
  data () {
    return {
      activeIndex: '0',
    };
  },
};
</script>

<style lang="stylus">
.el-menu-item.is-active {
  border-bottom: 3px solid $accentColor !important;
}
</style>