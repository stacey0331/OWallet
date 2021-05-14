<template>
  <div id="app">
    <top-left-nav v-if="$route.name !== 'Home'"></top-left-nav>

    <div class="container-fluid">
      <router-view></router-view>
    </div>

      <loading-modal></loading-modal>
  </div>
</template>

<script>
  import 'bootstrap/dist/css/bootstrap.min.css'
  import 'bootstrap/dist/js/bootstrap.min.js'
  import TopLeftNav from "./components/TopLeftNav"
  import LoadingModal from './components/Modals/Loading'

  export default {
    name: 'ont-wallet-test',
    components: {TopLeftNav, LoadingModal},
    watch: {
      '$route': 'hideLoadingPage'
    },
    created() {
      if(!localStorage.getItem('net')) { // initialize the network as MAIN_NET
          localStorage.setItem('net', 'MAIN_NET');
      }
    },
    methods: {
      hideLoadingPage() {
        this.$store.dispatch('hideLoadingModals')
      }
    }
  }
</script>



<style lang="scss">
  @import 'ant-overwrite';
  /* CSS */
  :root {
    --black-or-white: black;
    --white-or-black: white;
    --primary-blue: #196BD8;
    --primary-blue-light: #619AE5;
    --primary-background: white;
    --primary-surface: #F5F7FB;
    --primary-surface-warm: #F4F4F6;
    --bright-text: #43474b;
    --medium-text: #6e747a;
    --light-border: 1px solid #f0f0f5;
    --box-shadow: #F2F2F2;
  }
  .darkmode--activated {
    --black-or-white: white;
    --white-or-black: black;
    --primary-background: black;
    --primary-surface: #1E1E1E;
    --primary-surface-warm: #2c2a2a;
    --bright-text: #cecece;
    --medium-text: #9c9c9c;
    --light-border: 1px solid #2A2A2A;
    --box-shadow: #525252;
  }

  @font-face {
    font-family: SourceSansPro;
    src: url('./assets/fonts/SourceSansPro-Semibold.ttf');
  }

  @font-face {
    font-family: AvenirNext-Bold;
    src: url('./assets/fonts/AvenirNextBold.ttf');
  }
  @font-face {
    font-family: AvenirNext-Medium;
    src: url('./assets/fonts/AvenirNextMedium.ttf');
  }
  @font-face {
    font-family: AvenirNext-Regular;
    src: url('./assets/fonts/avenirnextregular.otf');
  }
  
  @mixin dark-form-fields {
    border: none !important;
    background: rgb(70, 70, 70) !important;
    color: white;

    &:focus {
      box-shadow: 0 0 3px 2px var(--primary-blue);
    }
  }

  body {
      p {
        margin:0;
    }
  }

  .home-container,
  .content-container,
  .setting-container,
  .json-import-container,
  .detail-container,
  .auth-login,
  .list-container,
  .input-container,
  .ledger-import-container,
  .nav-item {
    isolation: isolate;
  }

  .app-container {
    isolation: isolate;
    width: 550px;
    margin: 0 auto;
    margin-top: 20px;
  }

  .loading {
    text-align: center;
    background: rgba(0, 0, 0, 0.05);
    width: 100%;
    height: 100%;
  }

  .container-fluid {
    padding-left: 5.13rem !important;
    padding-top: 4rem;
  }

  .font-regular {
    font-family: AvenirNext-Regular;
    color: var(--black-or-white);
    font-size: 0.88rem;
  }

  .font-gray {
    color: #6F7781;
  }

  .font-medium {
    font-family: AvenirNext-Medium;
    color: var(--bright-text) !important;
    font-size: 0.88rem;
  }

  .font-medium-black {
    font-family: AvenirNext-Medium;
    color: var(--black-or-white);
    font-size: 0.88rem;
  }

  .font-bold {
    font-family: AvenirNext-Bold;
    color: var(--medium-text);
    font-size: 14px;
  }

  .font-title {
    font-size:18px;
    font-family: AvenirNext-Regular,AvenirNext;
    font-weight:400;
    color: var(--black-or-white) !important;
  }


  /* Button CSS */
  .btn-container {
    width: 540px;
    margin: 25px auto;
  }

  .btn-next,
  .btn-cancel {
    min-width: 6.25rem !important;
    height: 2.13rem !important;
    font-family: AvenirNext-Medium !important;
    font-size: 14px !important;
    text-align: center !important;
  }

  .btn-cancel {
    background: #F5F7FB !important;
    border-radius: 0 !important;
    color: #5E6369 !important;
    border: none !important;
  }
  .btn-cancel:hover {
      background: #E4E6EA !important;
  }

  .btn-next {
    background: var(--primary-blue) !important;
    border-radius: 0 !important;
    border: none !important;

    &:hover {
      background: var(--primary-blue-light) !important;
    }
  }

  .btn-add {
    width: 80px !important;
    height: 34px !important;
    background: #FBE45A !important;
    border-radius: 0 !important;
    font-family: 'AvenirNext-Bold' !important;
    border: none !important;
    font-size: 18px !important;
  }

  .btn-add:hover {
    border: 1px solid #FBE45A !important;
  }

  .btn-cancel span, .btn-next span {
    width: 100%;
  }

  .input {
    border-radius: 0 !important;
    border: 1px solid #DFE2E9 !important;
    border-radius: 5px !important;
    height: 34px !important;
    color: var(--bright-text);
  }

  .darkmode--activated .input {
    @include dark-form-fields;
  }

  .textarea {
    background: transparent !important;
    border-radius: 5px !important;
    color: var(--bright-text);
  }

  .darkmode--activated .textarea {
    @include dark-form-fields;
  }

  .error-input {
    border-color:red !important;
  }

  .footer-btns {
    position: fixed;
    bottom: 0;
    width: calc(100% - 4rem);
    height: 85px;
    left: 4rem;
    box-shadow: 0 -1px 6px 0 var(--box-shadow);
    z-index: 1000;
  }

  .footer-btn-container {
    width: 540px;
    margin: 20px auto;
  }

  .footer-btn-container :last-child {
    float: right;
  }

  .ant-spin-text {
    color: white !important;
    text-shadow: none !important;
  }

  .v-validate-span-errors {
    color: red;
    font-size: 12px;
    display: block;
  }

  .refresh-icon {
    display: inline-block;
    background-image: url('./assets/refresh.svg');
    background-size: cover;
  }
  .add-icon {
    background-image: url('./assets/add.svg');
    display:inline-block;
    background-size: cover;
  }
  /* .add-icon:hover {
    background-image: url('./assets/add-hover.png');
  } */

  .common-icon {
    width:20px;
    height:20px;
    border-radius: 50%;
    background-color:#F4F4F6;
    cursor: pointer;
  }
  .darkmode--activated .common-icon {
    filter: brightness(2);
    background-color: #181818;
  }
  .common-icon:hover {
    background-color:#E4E6EA;
  }

  .copy-icon {
    display: inline-block;
    margin-left: 10px;
    background-image: url('./assets/copy_new.svg');
    background-size: cover;
    position: relative;
    top: 5px;
}

  .asset-container {
    height:40vh;
    overflow:auto;
  }

.asset-container::-webkit-scrollbar {
    -webkit-appearance: none;
}

.asset-container::-webkit-scrollbar:vertical {
    width: 10px;
    height:15px;
}

.asset-container::-webkit-scrollbar-thumb {
    border-radius: 4px;
    border: 2px solid white; /* should match background, can't be transparent */
    background-color:#dddddd;
}

 .wallet-balance {
    font-size: 16px;
    color: var(--black-or-white);
    font-family: 'AvenirNext-Bold';
    position: relative;
    margin-top: 30px;
    display: flex;
    justify-content: space-between;
    padding-bottom: 5px;
    border-bottom: var(--light-border);
  }

  .wallet-balance :first-child {
    float: left;
    margin-right: 20px;
  }


  .asset-item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    /* margin-top: 10px; */
    /* padding-right:20px; */
    width:100%;
    height:40px;
    border-bottom: var(--light-border);
  }

  .asset-ong {
    height: 2.56rem;
    line-height: 2.56rem;
    margin-top: 12px;
  }

  .asset-label {
    font-family: AvenirNext-Medium;
    font-size: 0.88rem;
    color: var(--black-or-white);
    opacity: 0.8;
    float: left;
    margin-right: 12px;
  }

  .asset-amount {
    font-family: AvenirNext-Medium;
    font-size: 18px;
    color: var(--black-or-white);
    opacity: 0.8;
  }

  .asset-value {
    padding-left: 3rem;
    font-family: AvenirNext-Medium;
    font-size: 14px;
    color: #000000;
    margin-bottom: 20px;
  }

  .asset-btn {
    border-radius: 0;
    background: var(--primary-blue);
    font-family: AvenirNext-Medium;
    font-size: 14px;
    color: #fff;
    margin-right: 20px;
    margin-bottom: 20px;
    border: none;
    width: 120px;
    height: 34px;
  }
  .text-btn-hover {
    &:hover {
      color: var(--primary-blue-light) !important;
    }
  }
  .asset-btn > i {
      margin-right: 4px;
  }

  .claim-ong-container {
    display:flex;
    justify-content: space-between;
    align-items: flex-end;
    padding-bottom:10px;
    border-bottom: var(--light-border);
    margin-bottom:20px;
  }

  .claim-ong-item {
    margin-bottom: 10px;
    position: relative;
  }

  .claim-ong-item :first-child {
    font-family: AvenirNext-Medium;
    font-size: 12px;
    color: var(--black-or-white);
    opacity: 0.3;
    margin-right: 8px;
    width: 100px;
    display: block;
    float: left;
  }

  .claim-ong-item :nth-child(2) {
    font-family: AvenirNext-Medium;
    font-size: 12px;
    color: var(--black-or-white);
    opacity: 0.3;
    float: left;
  }
  .redeem-container {
    display: flex;
    align-items: center;
  }

  .btn-redeem {
    border: none;
    color: var(--primary-blue) !important;
    font-size: 14px;
    font-family: AvenirNext-Medium;
    font-weight: 500;
    padding-right: 0;

    &:active {
      outline: none;
    }

    &:hover {
      color: var(--primary-blue-light) !important;
    }
  }

  .tx-item {
    display: flex;
    justify-content: space-between;
    margin-bottom:14px;
    font-family: AvenirNext-Medium;
    font-size: 12px;
    width:100%;
    cursor: pointer;
  }

  .tx-item:hover span {
    color: var(--primary-blue) !important;
  }

  .tx-item :first-child {
    flex: 0.6;
    overflow: hidden;
    text-overflow: ellipsis;
    color: #6F7781;
  }

  .tx-item :last-child {
    flex:0.4;
    text-align: right;
    font-family: AvenirNext-Medium;
    font-size: 12px;
    color: #000000;
  }

  .left-footer {
    margin-top: 20px;
  }
  .negative-margin-top {
    margin-top: -4rem;
  }

  .switch-btn {
    background: transparent;
    color: var(--bright-text);

    &:hover {
      color: var(--primary-blue);
      border-color: var(--primary-blue);
    }
  }

  .tx-title {
      font-size: 18px;
      font-weight: 500;
      margin-bottom: 15px;
      color: var(--black-or-white);
  }

  .label-left {
      width: 200px;
      margin-right: 10px;
      @extend .fields-label;
  }

  .fields-label {
    color: var(--bright-text) !important;
  }

  td {
    color: var(--medium-text);
  }

  thead tr th {
    background: var(--primary-surface) !important;

    div {
      color: var(--bright-text);
    }
  }

  .payer-radio-item {
    margin-bottom: 20px;
    color: var(--bright-text);
  }
  
  .selection-item > p {
    color: var(--black-or-white) !important;
  }


  .darkmode--activated .ant-select-selection {
    @include dark-form-fields;
    .ant-select-arrow {
      color: var(--bright-text);
    }
  }
</style>
