<script lang="ts" setup>
import { ref } from 'vue';
import { useSettingsStore } from '@/store/modules/settings';

const settingsStore = useSettingsStore();

defineProps({
  collapse: {
    type: Boolean,
    required: true
  }
});

const logo = ref<string>(
  new URL(`../../../assets/logo.png`, import.meta.url).href
);
</script>

<template>
  <transition color="bg-transparent">
    <router-link
      v-if="collapse"
      key="collapse"
      class="h-[50px] flex items-center justify-center"
      to="/"
    >
      <img v-if="settingsStore.sidebarLogo" src="@/assets/jnu.jpeg" class="w-5 h-5" />
      <h1 v-else>区块链实训平台</h1>
    </router-link>

    <router-link
      v-else
      key="expand"
      class="h-[50px] flex items-center justify-center"
      to="/"
    >
      <img v-if="settingsStore.sidebarLogo" src="@/assets/jnu.jpeg" class="w-5 h-5" />
      <span class="ml-3  text-sm font-400">区块链实训平台</span>
    </router-link>
  </transition>
</template>


    
