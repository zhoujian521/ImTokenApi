<template>
  <q-page class="flex flex-center">
    <q-btn color="primary" label="scanQRCode" @click="scanQRCode" />
  </q-page>
</template>

<style></style>

<script>
export default {
  name: "PageIndex",
  mounted() {
    window.addEventListener("load", async () => {
      if (window.ethereum) {
        console.log("====window.ethereum====");
        console.log(window.ethereum);
        console.log("====window.ethereum====");
        this.isImToken();
      } else if (window.web3) {
        console.log("====window.web3=====");
        console.log(window.web3);
        console.log("====window.web3======");
        this.isImToken();
      }
    });
  },
  methods: {
    isImToken() {
      if (!!window.imToken || window.ethereum.isImToken) {
        console.log("isImToken ===> true");
        const message = "isImToken ===> true";
        this.$q.notify({
          message,
          position: "top",
          color: "positive",
          timeout: 2000
        });
      } else {
        console.log("isImToken ===> false");
        const message = "isImToken ===> false";
        this.$q.notify({
          message,
          position: "top",
          color: "positive",
          timeout: 2000
        });
      }
    },
    scanQRCode() {
      try {
        console.log("============window.imToken========================");
        console.log(window.imToken);
        console.log("============window.imToken========================");
        console.log("========001====native.scanQRCode========================");
        window.imToken.callAPI("native.scanQRCode", function(err, text) {
          if (err) {
            alert(err.message);
            console.log("====native.scanQRCode==err===");
            console.log(err.message);
            console.log("====native.scanQRCode==err====");
            this.$q.notify({
              message: err.message,
              position: "top",
              color: "positive",
              timeout: 2000
            });
          } else {
            alert(text);
            console.log("====native.scanQRCode===success==");
            console.log(text);
            console.log("====native.scanQRCode===success===");
            this.$q.notify({
              message: text,
              position: "top",
              color: "positive",
              timeout: 2000
            });
          }
        });
        console.log("======002=====native.scanQRCode=========================");
      } catch (error) {
        console.log("============native.scanQRCode========================");
        console.log(error);
        console.log("============native.scanQRCode========================");
      }
    }
  }
};
</script>
