<template>
	<div :class="[`nav-theme-${navTheme}`, `nav-layout-${navLayout}`]">
		<a-layout id="components-layout-demo-side" style="min-height: 100vh">
    <a-layout-sider :trigger="null" v-if="navLayout === 'left'" :theme="navTheme"
      collapsible
      v-model="collapsed"  width='256px'
    >
      <div class="logo">ant design vue pro</div>
      <SiderMenu :theme="navTheme"/>
    </a-layout-sider>
    <a-layout>
      <a-layout-header style="background: #fff; padding: 0" >
		  <a-icon
          class="trigger"
          :type="collapsed ? 'menu-unfold' : 'menu-fold'"
          @click="()=> collapsed = !collapsed"
        />
	  <Header/>
	  </a-layout-header>
      <a-layout-content style="margin: 0 16px">
        <router-view></router-view>
      </a-layout-content>
      <a-layout-footer style="text-align: center">
        <Footer/>
      </a-layout-footer>
    </a-layout>
  </a-layout>
  <SettingDrawer/>
	</div>
</template>

<script>
	import Header from "./Header.vue"
	import Footer from "./Footer.vue"
	import SiderMenu from "./SiderMenu.vue"
	import SettingDrawer from "../components/SettingDrawer/index.vue"
	export default{
		data() {
			return {
			  collapsed: false,
			}
		  },
		  computed:{
		  	navTheme(){
		  		return this.$route.query.navTheme || 'dark';
		  	},
		  	navLayout(){
		  		return this.$route.query.navLayout || 'left';
		  	}
		  },
		components:{
			Header,
			Footer,
			SiderMenu,
			SettingDrawer
		}
	}
</script>
<style scoped="scoped">
#components-layout-demo-side .trigger {
  font-size: 18px;
  line-height: 64px;
  padding: 0 24px;
  cursor: pointer;
  transition: color .3s;
}

#components-layout-demo-side .trigger:hover {
  color: #1890ff;
}

#components-layout-demo-side .logo {
  height: 32px;
  background: rgba(255,255,255,.2);
  margin: 16px;
}
.nav-theme-dark .logo{
	line-height: 32px;
	color: #fff;
	text-align: center;
}
</style>
