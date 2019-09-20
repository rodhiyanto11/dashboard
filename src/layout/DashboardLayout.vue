<template>
  <div class="wrapper" :class="{ 'nav-open': $sidebar.showSidebar }">
    <side-bar
      :background-color="sidebarBackground"
      short-title="Argon"
      title="Argon"
    >
      <template slot="links">
        <sidebar-item
          :link="{
            name: 'Dashboard',
            icon: 'ni ni-tv-2 text-primary',
            path: '/dashboard'
          }"
        />

        <sidebar-item :link="{name: 'Icons', icon: 'ni ni-planet text-blue', path: '/icons'}"/>
        <sidebar-item :link="{name: 'Maps', icon: 'ni ni-pin-3 text-orange', path: '/maps'}"/>
        <sidebar-item :link="{name: 'User Profile', icon: 'ni ni-single-02 text-yellow', path: '/profile'}"/>
        <sidebar-item :link="{name: 'Tables', icon: 'ni ni-bullet-list-67 text-red', path: '/tables'}"/>
        <sidebar-item :link="{name: 'Login', icon: 'ni ni-key-25 text-info', path: '/login'}"/>
        <sidebar-item :link="{name: 'Register', icon: 'ni ni-circle-08 text-pink', path: '/register'}"/>
        <li to="/" tag="li" class="nav-item active"><a data-toggle="collapse" class="sidebar-menu-item nav-link active" aria-expanded="true"><i class="ni ni-shop text-primary"></i> <span class="nav-link-text">Dashboards <b class="caret"></b></span></a> <div class="collapse show" style="animation-fill-mode: both; animation-timing-function: ease-out;" data-old-padding-top="" data-old-padding-bottom="" data-old-overflow=""><ul class="nav nav-sm flex-column"><li class="nav-item active nuxt-link-active"><!----> <div class="collapse show" style="display: none;"><ul class="nav nav-sm flex-column"></ul></div> <a href="/dashboard" class="nav-link active nuxt-link-active"><span class="nav-link-text">Dashboard</span></a></li> <li class="nav-item"><!----> <div class="collapse show" style="display: none;"><ul class="nav nav-sm flex-column"></ul></div> <a href="/alternative" class="nav-link"><span class="nav-link-text">Alternative</span></a></li></ul></div> <!----></li>
      </template> 
    </side-bar>
    <div class="main-content" :data="sidebarBackground">
      <dashboard-navbar></dashboard-navbar>

      <div @click="toggleSidebar">
        <fade-transition :duration="200" origin="center top" mode="out-in">
          <!-- your content here -->
          <router-view></router-view>
        </fade-transition>
        <content-footer v-if="!$route.meta.hideFooter"></content-footer>
      </div>
    </div>
  </div>
</template>
<script>
  import DashboardNavbar from './DashboardNavbar.vue';
  import ContentFooter from './ContentFooter.vue';
  import { FadeTransition } from 'vue2-transitions';

  export default {
    components: {
      DashboardNavbar,
      ContentFooter,
      FadeTransition
    },
    data() {
      return {
        sidebarBackground: 'vue' //vue|blue|orange|green|red|primary
      };
    },
    methods: {
      toggleSidebar() {
        if (this.$sidebar.showSidebar) {
          this.$sidebar.displaySidebar(false);
        }
      }
    }
  };
</script>
<style lang="scss">
</style>
