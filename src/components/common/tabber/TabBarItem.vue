<template>
    <!-- 所有的item都展示同一个图片和文字 -->
    <div class="tab-bar-item" @click="itemClick">
      <div v-if="!isActive"><slot name="item-icon"></slot></div>
      <div v-else><slot name="item-icon-active"></slot></div>
      <!-- <div :class="{active: isActive}"><slot name="item-text"></slot></div> -->
      <div :style="activeStyle"><slot name="item-text"></slot></div>
      <!-- <img src="../../assets/img/tabbar/home.svg" alt="">
      <div>首页</div> -->
    </div>
</template>

<script>
export default {
  name: 'TabBarItem',
  props: {
    path: String,
    activeColor: {
      type: String,
      default: "red",
    }
  },
  data() {
    return {
      // isActive: true
    }
  },
  computed: {
    isActive() {
      return this.$route.path.indexOf(this.path) !== -1
    },
    activeStyle() {
      return this.isActive ? {color: this.activeColor} : {}
    }
  },
  methods: {
    itemClick() {
       this.$router.push(this.path)     
    }
  },
}
</script>

<style>

  .tab-bar-item {
    flex: 1;
    text-align: center;
    height: 49px;
    font-size: 14px;
  }

  .tab-bar-item img {
    width: 24px;
    height: 24px;
    margin: 3px 0 2px 0;
    vertical-align: middle;
  }

  /* .active {
    color: red;
  } */

</style>
