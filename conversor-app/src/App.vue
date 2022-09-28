<template>
  <h1 class="label-title">Reais para dolar</h1>

  <div class="div-convert">
    <span class="p-float-label">
      <InputText
        id="input-real"
        type="text"
        v-model="real"
        :disabled="convert"
      />
      <label for="input-real">Real</label>
    </span>
  </div>

  <div class="div-convert">
    <span class="p-float-label">
      <InputText
        id="input-dolar"
        type="text"
        v-model="dolar"
        :disabled="convert"
      />
      <label for="input-dolar">Dolar</label>
    </span>
  </div>

  <div class="div-convert" v-if="!convert">
    <Button label="Limpar" @click="clear" />
    <Button label="Calcular" @click="calculate" class="button-calculate" />
  </div>

  <div v-if="convert">
    <p class="label-result">Conversao:{{ convert }}</p>
    <p class="label-classification">
      Com {{ real }}Reais e possivel comprar {{ convert }} dolares a {{ dolar }}
    </p>
    <Button @click="clear" label="Calcular novamente" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      real: null,
      dolar: null,
      convert: null,
      classification: "",
    };
  },
  methods: {
    calculate: function () {
      this.real;
      this.dolar;
      this.convert = (this.real / this.dolar).toFixed(2);
    },
    clear() {
      this.real = null;
      this.dolar = null;
      this.convert = null;
      this.result = "";
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.div-convert {
  margin-top: 2rem;
}

.button-calculate {
  margin-left: 1rem !important;
}
.label-title {
  font-size: 2rem;
}
.label.subtitle {
  font-size: 1.1rem;
}
.label-result {
  font-size: 1.5rem;
}
.p-float-label {
  display: inline-block !important;
}
</style>
