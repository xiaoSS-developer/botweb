<template>
  <div class="home">
    <van-nav-bar title="信息">
      <template #right>
        <router-link :to="{ name: 'createMsg' }">
          <van-icon name="plus" size="18" />
        </router-link>
        <van-popover v-model:show="showPopover" placement="bottom-end">
          <div class="van-popover__action">
            <div class="van-popover__action-text">批量操作</div>
          </div>
          <div class="van-popover__action">
            <router-link class="van-popover__action-text" :to="{ name: 'favor' }">收藏</router-link>
          </div>
          <div class="van-popover__action">
            <router-link class="van-popover__action-text" :to="{ name: 'itcpIdx' }">拦截信息</router-link>
          </div>
          <div class="van-popover__action">
            <router-link class="van-popover__action-text" :to="{ name: 'settingInfo' }">信息设置</router-link>
          </div>
          <template #reference>
            <van-icon class="icon-ellipsis-transform" name="ellipsis" size="18" />
          </template>
        </van-popover>
      </template>
    </van-nav-bar>
    <van-search v-model="searchVal" placeholder="请输入搜索关键词" />
    <van-list>
      <van-cell title="应用号" is-link :to="{name: 'application'}" />
      <van-cell title="通知类消息" is-link :to="{name: 'notice'}" />
      <van-cell v-for="item in list" :key="item" :title="item.name" :value="item.time" :label="item.desc" is-link :to="{ name: 'viewMsg', params: { userId: item.name } }" />
    </van-list>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component'
import { NavBar, Icon, Search, Popover, List, Cell } from 'vant'

@Options({
  components: {
    [Icon.name]: Icon,
    [NavBar.name]: NavBar,
    [Search.name]: Search,
    [Popover.name]: Popover,
    [List.name]: List,
    [Cell.name]: Cell,
  },
})
export default class Home extends Vue {
  private showPopover = false
  private searchVal = ''
  private list = [
    { name: 'Ue4', time: '上午10:20', desc: '滚滚滚' },
    { name: 'Ue5', time: '上午10:21', desc: '滚滚滚' },
    { name: 'Ue6', time: '上午10:22', desc: '滚滚滚' },
  ]
}
</script>
