<template>
  <q-layout view="lHh Lpr lFf">
    <q-header>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="leftDrawerOpen = !leftDrawerOpen"
        />


      </q-toolbar>
      <div class= "q-px-lg q-pt-xl q-mb-md">

      </div>
      <div class="q-px-lg q-pt-xl q-mb-md">
        <div class = "text-h3">ToDo</div> 
        <div class="text-subtitle1">{{todaysDate}}</div>
      </div>
    <q-img src="statics/mountains.jpg" class="header-image absolute-top"></q-img>
    </q-header>

         <q-drawer
        v-model="leftDrawerOpen"
        show-if-above
        :width="250"
        :breakpoint="600"
      >
        <q-scroll-area style="height: calc(100% - 256px); margin-top: 256px; border-right: 1px solid #ddd">
          <q-list padding>
            <q-item to="/"
            clickable v-ripple
            exact>

              <q-item-section avatar>
                <q-icon name="list" />
              </q-item-section>

              <q-item-section>
                To-Do
              </q-item-section>
            </q-item>
            <q-item to="/help"
            clickable v-ripple
            exact>
              <q-item-section avatar>
                <q-icon name="help" />
              </q-item-section>

              <q-item-section>
                Help
              </q-item-section>
            </q-item>


          </q-list>
        </q-scroll-area>

        <q-img class="absolute-top" src="statics/mountains.jpg" style="height: 256px">
          <div class="absolute-bottom bg-transparent">
            <q-avatar size="80px" class="q-mb-sm">
              <img src="statics/lipuchen.jpg">
            </q-avatar>
            <div class="text-weight-bold">Li-Pu Chen</div>
            <div>@lipuchen</div>
          </div>
        </q-img>
      </q-drawer>


    <q-page-container>
      <keep-alive>
        <router-view />
      </keep-alive>
    </q-page-container>
  </q-layout>
</template>

<script>
import { date } from 'quasar'
import EssentialLink from 'components/EssentialLink'

export default {
  name: 'MainLayout',

  components: {
    EssentialLink
  },

  data () {
    return {
      leftDrawerOpen: false,
      essentialLinks: [
        {
          title: 'Docs',
          caption: 'quasar.dev',
          icon: 'school',
          link: 'https://quasar.dev'
        },
        {
          title: 'Github',
          caption: 'github.com/quasarframework',
          icon: 'code',
          link: 'https://github.com/quasarframework'
        },
        {
          title: 'Discord Chat Channel',
          caption: 'chat.quasar.dev',
          icon: 'chat',
          link: 'https://chat.quasar.dev'
        },
        {
          title: 'Forum',
          caption: 'forum.quasar.dev',
          icon: 'record_voice_over',
          link: 'https://forum.quasar.dev'
        },
        {
          title: 'Twitter',
          caption: '@quasarframework',
          icon: 'rss_feed',
          link: 'https://twitter.quasar.dev'
        },
        {
          title: 'Facebook',
          caption: '@QuasarFramework',
          icon: 'public',
          link: 'https://facebook.quasar.dev'
        },
        {
          title: 'Quasar Awesome',
          caption: 'Community Quasar projects',
          icon: 'favorite',
          link: 'https://awesome.quasar.dev'
        }
      ]
    }
  },
  computed:{
    todaysDate(){
      let newDate = date.buildDate({ year:2010, date:5, hours:15, milliseconds:123})
      return newDate
    }
  }
}
</script>

<style lang="scss">
  .header-image{
    height: 100%;
    z-index: -1;
    opacity: 0.2;
    filter: grayscale(100%);
  }
</style>
