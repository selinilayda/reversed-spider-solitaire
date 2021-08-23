<script>
export default {
  name: "modalWin-component",
};
</script>

<template>
  <transition name="modal">
    <div class="modal__mask">
      <div class="modal__wrapper">
        <div class="modal__container">
          <div class="modal__header">
            <h3 class="modal__title">
              Congratulations!
            </h3>
            <button
              type="button"
              class="modal__button button button--exit"
              @click="$emit('close')"
            >
              x
            </button>
          </div>

          <div class="modal__body">
            <slot name="body">
              You have won this game!
            </slot>
          </div>

          <div class="modal__footer">
            <slot name="footer">
              <button
                @click="
                  $emit('close');
                  $emit('newGame');
                "
                class="modal__button button button--newGame"
                type="button"
              >
                New Game
              </button>
            </slot>
          </div>
        </div>
      </div>
    </div>
  </transition>
</template>

<style scoped>
.modal__mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: table;
  transition: opacity 0.3s ease;
}
.modal__wrapper {
  display: table-cell;
  vertical-align: middle;
}
.modal__container {
  width: 400px;
  margin: 0px auto;
  padding: 20px 30px;
  background-color: #fff;
  border-radius: 10px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
  transition: all 0.3s ease;
  font-family: Helvetica, Arial, sans-serif;
}
.modal__header {
  display: flex;
  align-items: center;
}
.modal__title {
  margin-top: 0;
  flex: 1;
}
.modal__body {
  margin: 50px 0;
}
.button {
  padding: 5px 12px;
  border-radius: 5px;
  cursor: pointer;
}
.button--exit {
  background-color: #b70000;
  color: white;
  border: none;
}
.button--exit:hover {
  background-color: #333;
}
.button--newGame {
  background-color: #79ed6f;
  border: 2px solid #03a500;
  padding: 10px 22px;
}
.button--newGame:hover {
  background-color: #03a500;
}
.modal-enter,
.modal-leave-active {
  opacity: 0;
}
.modal-enter .modal-container,
.modal-leave-active .modal-container {
  -webkit-transform: scale(1.1);
  transform: scale(1.1);
}
</style>
