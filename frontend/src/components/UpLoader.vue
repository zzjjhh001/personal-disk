<template>
  <uploader
    :options="options"
    :file-status-text="statusText"
    class="uploader-example"
    ref="uploaderRef"
    @file-complete="fileComplete"
    @complete="complete"
  >
    <!-- <uploader-unsupport></uploader-unsupport>
    <uploader-drop>
      <p>Drop files here to upload or</p>
      <uploader-btn>select files</uploader-btn>
      <uploader-btn :attrs="attrs">select images</uploader-btn>
      <uploader-btn :directory="true">select folder</uploader-btn>
    </uploader-drop>
    <uploader-list></uploader-list> -->
  </uploader>
</template>

<script setup>
import { nextTick, ref, onMounted } from 'vue'
import { upLoaderOptions as options } from '../utils/constant.js'
const uploaderRef = ref(null)
const attrs = {
  accept: 'image/*'
}
const statusText = {
  success: 'success',
  error: 'error',
  uploading: 'uploading',
  paused: 'paused',
  waiting: 'waiting'
}
const complete = () => {
  console.log('complete', arguments)
}
const fileComplete = () => {
  console.log('file complete', arguments)
}
onMounted(() => {
  nextTick(() => {
    window.uploader = uploaderRef.value.uploader
  })
})
</script>

<style>
  .uploader-example {
    width: 880px;
    padding: 15px;
    margin: 40px auto 0;
    font-size: 12px;
    box-shadow: 0 0 10px rgba(0, 0, 0, .4);
  }
  .uploader-example .uploader-btn {
    margin-right: 4px;
  }
  .uploader-example .uploader-list {
    max-height: 440px;
    overflow: auto;
    overflow-x: hidden;
    overflow-y: auto;
  }
</style>