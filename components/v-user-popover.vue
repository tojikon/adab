<template>
  <el-popover
    class="v-user-popover"
    placement="bottom"
    width="300"
    trigger="click"
  >
    <el-button slot="reference" class="v-user-popover__reference" circle>
      <img class="v-user-popover__reference--image" src="../assets/images/avatar.png" alt="Img">
    </el-button>

    <div class="v-user-popover__container">
      <img class="v-user-popover__container--image" src="../assets/images/avatar.png" alt="Img">
      <h3 class="v-user-popover__container--name">Shamil Kurbonov</h3>
      <cDayNightToggle class="v-user-popover__container--day-night"/>
      <nuxt-link to="settings"><el-button><i class="el-icon-setting"/> Settings</el-button></nuxt-link>
      <el-button @click.prevent="logout"><i class="el-icon-pear"/>Log out</el-button>
    </div>

  </el-popover>
</template>

<script>
    import cDayNightToggle from "./c-day-night-toggle"

    export default {
      name: "v-user-popover",
      components: {
        cDayNightToggle
      },
      methods: {
        logout() {
          this.$store.dispatch('logout')
          this.$router.push('/login')
        }
      }
    }
</script>

<style lang="scss">
  .v-user-popover {

    &__reference {
      background: none;
      border: none;
      padding: 0;
      line-height: 0;
      &:hover, &:focus {
        background: none;
      }
      &.is-circle {
        padding: 0;
      }

      &--image {
        width: 40px;
        height: 40px;
        padding: 2px;
        border-radius: 50%;
        border: 1px solid var(--app-border-menu);
        &:hover, &:focus {
          transition: 0.25s;
          border: 1px solid $blue;
        }
      }
    }

    &__container {
      margin: 0 auto;
      text-align: center;

      &--image {
        width: 60px;
        height: 60px;
        border-radius: 50%;
        border: 1px solid var(--app-border-menu);
        padding: 3px;
      }
      &--name {

      }
      &--day-night {
        display: block;
        margin: 6px auto;
      }

     }

    .el-button {
      background: var(--app-background);
      color: var(--app-text-color);
    }
  }

  // Default style element-ui

  .el-popover {
    border-color: var(--app-border-menu);
    background-color: var(--app-background);
    margin-top: 9px !important;
  }
  .popper__arrow, .popper__arrow::after {
    border-bottom-color: var(--app-border-menu) !important;
  }
</style>
