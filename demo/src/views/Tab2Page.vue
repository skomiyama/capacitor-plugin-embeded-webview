<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Tab 2</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Tab 2</ion-title>
        </ion-toolbar>
      </ion-header>
      
      <ExploreContainer name="Tab 2 page" />
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent } from '@ionic/vue';
import { EmbeddedWebview, EmbeddedWebviewOptions } from '@skomiyama/embedded-webview';
import ExploreContainer from '@/components/ExploreContainer.vue';

export default defineComponent({
  name: 'Tab2Page',
  components: { ExploreContainer, IonHeader, IonToolbar, IonTitle, IonContent, IonPage },
  async mounted() {
    const options: EmbeddedWebviewOptions = {
      url: 'https://twogate.com',
      webviewConfiguration: {
        width: (this.$el as HTMLElement).clientWidth,
        height: (this.$el as HTMLElement).clientHeight,
      }
    }
    await EmbeddedWebview.create(options);
  },
  async ionViewDidEnter() {
    console.log(await EmbeddedWebview.show());
  },
  async ionViewDidLeave() {
    console.log(await EmbeddedWebview.hide());
  }
});
</script>
