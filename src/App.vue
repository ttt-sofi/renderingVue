<template>
  <div class="row align-items-center">
    <div class="container col-6 mt-5" style="width: 500px">
      <form>
        <!-- color de texto DONE -->
        <div class="mb-3">
          <label for="colordetexto" class="form-label">Color de Texto</label>
          <input
            type="text"
            class="form-control"
            id="colordetexto"
            v-model="color"
          />
        </div>

        <!-- color de fondo DONE -->
        <div class="mb-3">
          <label for="colordefondo" class="form-label">Color de fondo</label>
          <input
            type="text"
            class="form-control"
            id="colordefondo"
            v-model="backgroundColor"
          />
        </div>

        <!-- mostrar DONE  -->
        <div class="mb-3 form-check">
          <input
            type="checkbox"
            class="form-check-input"
            id="Mostrar"
            v-model="mostrar"
          />
          <label class="form-check-label" for="Mostrar">Mostrar texto</label>
        </div>

        <!-- borde DONE -->
        <div class="mb-3 form-check">
          <input type="range" class="form-range" id="borde" v-model="borde" />
          <label class="form-range" for="borde">Borde</label>
        </div>

        <!-- Contenido texto: DONE -->
        <div class="mb-3">
          <label for="ContenidoTexto" class="form-label">Contenido Texto</label>
          <input
            type="text"
            class="form-control"
            id="ContenidoTexto"
            v-model="textoCaja"
          />
        </div>

        <!-- Tipografia DONE -->
        <div class="mb-3">
          <label class="form-label">Elige una tipografía:</label>

          <select class="form-select" v-model="tipografiaselected">
            <option v-for="tipografia in tipografias">{{ tipografia }}</option>
          </select>
        </div>

        <!-- OPACIDAD DONE -->
        <div class="mb-3 form-check">
          <input
            type="checkbox"
            class="form-check-input"
            id="opacidad"
            v-model="opacidad"
          />
          <label class="form-check-label" for="opacidad">Opaco</label>
        </div>

        <!-- TAMAÑO DEL LETRA DONE -->
        <div class="container mt-3">
          <p>Tamaño de letra</p>
          <div class="d-flex align-items-center gap-3">
            <label class="form-check-label">
              <input class="form-check-input" type="radio" v-model="selectedFontSize" value="16" />
              Tamaño pequeño (16px)
            </label>

            <label class="form-check-label">
              <input class="form-check-input" type="radio" v-model="selectedFontSize" value="24" />
              Tamaño mediano (24px)
            </label>

            <label class="form-check-label">
              <input class="form-check-input" type="radio" v-model="selectedFontSize" value="32" />
              Tamaño grande (32px)
            </label>
          </div>
        </div>

      </form>
    </div>

    <div class="col-6">
      <div
        class="cajita d-flex justify-content-center align-items-center"
        :style="{
          'border-width': borde + 'px',
          'background-color': backgroundColor,
        }"
      >
        <p
          :style="{
            color: color,
            fontFamily: tipografiaselected,
            opacity: opacidad ? 0.5 : 1,
            fontSize: selectedFontSize + 'px',
          }"
          v-show="mostrar"
        >
          {{ textoCaja }}
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      mostrar: true,
      borde: 10,
      backgroundColor: "red",
      color: "blue",
      textoCaja: "Hola Mundo",
      tipografias: ["Arial", "Helvetica", "Times New Roman"],
      tipografiaselected: "",
      selectedFontSize: 16,
      opacidad: false,
    };
  },
};
</script>

<style>
.cajita {
  width: 200px;
  height: 200px;
  background-color: rgb(255, 255, 255);
  border: 1px solid black;
  border-radius: 10px;
}
</style>
