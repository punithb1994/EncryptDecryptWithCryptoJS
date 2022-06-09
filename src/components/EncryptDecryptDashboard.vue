<template>
  <div class="container-fluid m-1">
    <h4 class="text-center mt-3 mb-1">{{ msg }}</h4>
    <div class="row mt-2">
      <div class="col-12 mb-2">
        <div class="form-group">
          <label for="encryption_decryption_key"
            >Encryption - Decryption Key</label
          >
          <input
            type="text"
            class="form-control"
            v-model="encryption_decryption_key"
            id="encryption_decryption_key"
          />
        </div>
      </div>
      <div class="col-md-6 col-sm-12 mb-2">
        <div class="form-group">
          <label for="text_to_encrypt">Text to Encrypt</label>
          <input
            type="text"
            class="form-control"
            id="text_to_encrypt"
            @input="encryptText"
          />
        </div>
        <div class="form-group">
          <label for="encrypted_text">Encrypted Text</label>
          <input
            type="text"
            class="form-control"
            id="encrypted_text"
            readonly
            :value="this.encrypted_text"
          />
        </div>
      </div>

      <div class="col-md-6 col-sm-12 mb-2">
        <div class="form-group">
          <label for="text_to_decrypt">Text to Decrypt</label>
          <input
            type="text"
            class="form-control"
            id="text_to_decrypt"
            @input="decryptText"
          />
        </div>
        <div class="form-group">
          <label for="decrypted_text">Decrypted Text</label>
          <input
            type="text"
            class="form-control"
            id="decrypted_text"
            readonly
            :value="this.decrypted_text"
          />
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import CryptoJS from "crypto-js";
export default {
  name: "EncryptDecryptDashboard",
  props: {
    msg: String,
  },
  data() {
    return {
      encrypted_text: "",
      decrypted_text: "",
      encryption_decryption_key: "punithbandodekar",
    };
  },
  computed: {},
  created() {},
  watch: {},
  mounted() {},
  methods: {
    encryptText(event) {
      console.log("Encryption Key" + this.encryption_decryption_key);
      this.encrypted_text = CryptoJS.AES.encrypt(
        event.target.value,
        this.encryption_decryption_key
      );
    },
    decryptText(event) {
      console.log("Decryption Key" + this.encryption_decryption_key);
      this.decrypted_text = CryptoJS.AES.decrypt(
        event.target.value,
        this.encryption_decryption_key
      ).toString(CryptoJS.enc.Utf8);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
