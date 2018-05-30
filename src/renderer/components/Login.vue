<template>
  <div id="wrapper">
    <img id="logo" src="~@/assets/logo.png" alt="electron-vue">
    <main>
      <div style="">
      <el-radio-group v-model="formType" size="small">
        <el-radio-button label="login">登录</el-radio-button>
        <el-radio-button label="register">注册</el-radio-button>
      </el-radio-group>
      <div style="margin: 20px;"></div>
      <el-form label-position="left" label-width="100px" :model="formData">
        <el-form-item label="账号">
          <el-input v-model="formData.account"></el-input>
        </el-form-item>
        <el-form-item label="密码">
          <el-input v-model="formData.password"></el-input>
        </el-form-item>
        <div v-if="formType == 'register'">
          <el-form-item label="确认密码">
            <el-input v-model="formData.confirmPassword"></el-input>
          </el-form-item>
          <el-form-item label="姓">
            <el-input v-model="formData.firstName"></el-input>
          </el-form-item>
          <el-form-item label="名">
            <el-input v-model="formData.lastName"></el-input>
          </el-form-item>
          <el-form-item label="年龄">
            <el-input v-model="formData.age"></el-input>
          </el-form-item>
          <el-form-item label="手机号">
            <el-input v-model="formData.phone"></el-input>
          </el-form-item>
          <el-form-item label="ethereum地址">
            <el-input v-model="formData.ethereumAddress"></el-input>
          </el-form-item>
        </div>
        <el-form-item v-if="formType == 'login'">
          <el-button type="primary" @click="login" class="loginBtn">登录</el-button>
        </el-form-item>
        <el-form-item v-else>
          <el-button type="primary" @click="submitForm('ruleForm2')" class="loginBtn">提交</el-button>
          <el-button @click="resetForm('ruleForm2')" class="loginBtn">重置</el-button>
        </el-form-item>
      </el-form>
      </div>
    </main>
  </div>
</template>

<script>
  import SystemInformation from './LandingPage/SystemInformation';

  export default {
    name: 'landing-page',
    components: { SystemInformation },
    methods: {
      open(link) {
        this.$electron.shell.openExternal(link);
      },
      submitForm() {
        console.log('submitForm');
      },
      resetForm() {
        console.log('resetForm');
      },
      login() {
        const that = this;
        const formData = that.$data.formData;
        console.log('login');
        const account = formData.account;
        console.log(account);
      },
    },
    data() {
      return {
        formType: 'login',
        formData: {
          account: '',
          password: '',
          confirmPassword: '',
          firstName: '',
          lastName: '',
          age: '',
          phone: '',
          ethereumAddress: '',
        },
      };
    },
  };
</script>

<style>
  @import url('https://fonts.googleapis.com/css?family=Source+Sans+Pro');

  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  body { font-family: 'Source Sans Pro', sans-serif; }

  #wrapper {
    background:
      radial-gradient(
        ellipse at top left,
        rgba(255, 255, 255, 1) 40%,
        rgba(229, 229, 229, .9) 100%
      );
    height: 200vh;
    padding: 60px 80px;
    width: 120vw;
  }

  #logo {
    height: auto;
    margin-bottom: 20px;
    width: 420px;
  }

  main {
    display: flex;
    justify-content: space-between;
  }

  main > div { flex-basis: 50%; }

  .left-side {
    display: flex;
    flex-direction: column;
  }

  .welcome {
    color: #555;
    font-size: 23px;
    margin-bottom: 10px;
  }

  .title {
    color: #2c3e50;
    font-size: 20px;
    font-weight: bold;
    margin-bottom: 6px;
  }

  .title.alt {
    font-size: 18px;
    margin-bottom: 10px;
  }

  .doc p {
    color: black;
    margin-bottom: 10px;
  }

  .doc button {
    font-size: .8em;
    cursor: pointer;
    outline: none;
    padding: 0.75em 2em;
    border-radius: 2em;
    display: inline-block;
    color: #fff;
    background-color: #4fc08d;
    transition: all 0.15s ease;
    box-sizing: border-box;
    border: 1px solid #4fc08d;
  }

  .doc button.alt {
    color: #42b983;
    background-color: transparent;
  }
  .loginBtn {
    width: 200px;
  }
</style>
