<template>
  <div>
    <NuxtWelcome />
  </div>
</template>

<script>
import {
  AppTrackingTransparency,
  AppTrackingStatusResponse,
} from 'capacitor-plugin-app-tracking-transparency';

export default {
  async mounted() {
    requestPermission();
// getStatus();

  },
};
async function getStatus() {
  try {
    const response = await AppTrackingTransparency.getStatus();
    console.log(response); // { status: 'authorized' } for example
    status.value = response;
  } catch (error) {
    console.error('Error getting status:', error);
  }
}

async function requestPermission() {
  try {
    const response = await AppTrackingTransparency.requestPermission();
    console.log(response); // { status: 'authorized' } for example
    status.value = response;
  } catch (error) {
    console.error('Error requesting permission:', error);
  }
}

</script>