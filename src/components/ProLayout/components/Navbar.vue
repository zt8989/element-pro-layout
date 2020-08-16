<template>
  <div class="navbar">
    <slot v-if="$scopedSlots.collapsedButtonRender" :collapsed="collapsed" name="collapsedButtonRender" />
    <hamburger v-else :is-active="!collapsed" class="hamburger-container" @toggleClick="toggleSideBar" />

    <slot v-if="$scopedSlots.breadcrumbRender" name="breadcrumbRender" />
    <breadcrumb v-else class="breadcrumb-container" />

    <slot name="rightContentRender" />
  </div>
</template>

<script>
import Breadcrumb from '@/components/Breadcrumb'
import Hamburger from '@/components/Hamburger'
import { headerProps } from '../props'

export default {
  components: {
    Breadcrumb,
    Hamburger
  },
  props: headerProps,
  methods: {
    toggleSideBar() {
      this.handleCollapse && this.handleCollapse()
    }
  }
}
</script>

<style lang="scss">
@import "../variables.scss";
.#{$proLayoutPrefix}-app-wrapper {
  .navbar {
    height: 50px;
    overflow: hidden;
    position: relative;
    background: #fff;
    box-shadow: 0 1px 4px rgba(0,21,41,.08);

    .hamburger-container {
      line-height: 46px;
      height: 100%;
      float: left;
      cursor: pointer;
      transition: background .3s;
      -webkit-tap-highlight-color:transparent;

      &:hover {
        background: rgba(0, 0, 0, .025)
      }
    }

    .breadcrumb-container {
      float: left;
    }
  }
}
</style>
