<template>
  <div class="cart-list">
    <scroll class="content" ref="scroll">
      <!--    列表-->
      <cart-list-item v-for="(item, index) in cartList"
                      :key="index"
                      :item-info="item"/>
    </scroll>
  </div>

</template>

<script>
import Scroll from 'components/common/scroll/Scroll.vue'

import CartListItem from './CartListItem'

  import {mapGetters} from 'vuex'

  export default {
    name: 'CartList',
    components: {
      Scroll,
      CartListItem,
    },
    computed: {
      ...mapGetters(['cartList'])
    },
    activated() { // 重新渲染高度
      this.$refs.scroll.refresh()
    }
  }

</script>
<style scoped>
.cart-list{
  height: calc(100% - 44px - 49px - 40px);
}
  .content{
    height: 100%;
    overflow: hidden;
  }
</style>
