<template>
  <div>

    <h1>Filtr adres</h1>

    <p>
      <label><input type="checkbox" v-model="showPraha">Praha</label>
    </p>
    <p>
      <label><input type="checkbox" v-model="showBrno">Brno</label>
    </p>
    <p>
      <label><input type="checkbox" v-model="showOstrava">Ostrava</label>
    </p>
<br />
<p>Zadejte novou adresu:</p>

    Město:<br /><input v-model="city"  /><br />
    Ulice:<br /><input v-model="street"  /><br />
    PSČ:<br /><input v-model="zip"   /><br />

    <button @click="createNewAdress">Odeslat</button>


    <h1>Adresy</h1>

    <div
      v-for="(val, index) of adresses"
      :key="index"
    >
      <p v-if="(showPraha && val.city === 'Praha')">
        {{ val.city + ": " + val.street + ", " + val.zip }}</p>
      <p v-if="(showBrno && val.city === 'Brno')">
          {{ val.city + ": " + val.street + ", " + val.zip }}</p>
      <p v-if="(showOstrava && val.city === 'Ostrava')">
          {{ val.city + ": " + val.street + ", " + val.zip }}</p>
    </div>

  </div>
</template>

<script>

export default {
  data () {
    let city = this.city;
    let street = this.street;
    let zip = this.zip;
    let adresses = [ 
        {
            city: "Praha",
            street: "Dlouhá 87",
            zip: "140 00"
         },
         {
            city: "Brno",
            street: "Krátká 4",
            zip: "650 00"
         },
        {
            city: "Ostrava",
            street: "Rovná 73",
            zip: "78 00"
         }
        ]
    return {
      showPraha: true,
      showBrno: true,
      showOstrava: true,
      adresses,
      city,
      street,
      zip
    }
  },
 methods: {
    createNewAdress: function () {
         this.adresses.push({city: this.city,street: this.street,zip: this.zip})
          
      }
  }
}
</script>

<style>

</style>
