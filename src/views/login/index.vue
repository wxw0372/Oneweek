<template>
  <div class="login-container">
    <div class="login-box">
      <h1>手机号登录</h1>
      <el-form
        :model="ruleForm"
        :rules="rules"
        ref="ruleForm"
        class="demo-ruleForm"
      >
        <el-form-item prop="mobile">
          <el-input v-model="ruleForm.mobile"></el-input>
        </el-form-item>
        <el-form-item prop="password">
          <el-input v-model="ruleForm.password"></el-input>
        </el-form-item>
        <el-form-item>
          <el-button class="login-btn" type="primary" @click="login"
            >登录</el-button
          >
        </el-form-item>
      </el-form>
    </div>
  </div>
</template>

<script>
export default {
  name: "Login",
  data() {
    return {
      ruleForm: {
        mobile: "13800000002",
        password: "hm#qd@23!",
      },
      rules: {
        mobile: [{ required: true, message: "请输入手机号", trigger: "blur" }],
        password: [{ required: true, message: "请输入密码", trigger: "blur" }],
      },
    };
  },
  methods: {
    async login() {
      this.$refs.ruleForm.validate(async (valid) => {
        if (valid) {
          this.$store.dispatch("user/login", this.ruleForm);
          // this.store.login(this.ruleForm)
          // const res = await loginApi(this.ruleForm);
          // this.$router.push("/");
          // console.log("res=>", res);
          // if(data.code === 200){
          //   this.$store.commit('setToken',data.data.token)
          //   this.$store.commit('setUserInfo',data.data.userInfo)
          //   this.$router.push('/home')
          // }
        }
      });
    },
  },
};
</script>

<style lang="scss">
.login-container {
  width: 100%;
  height: 100%;
  background: url("../../assets/common/login_back.png") no-repeat;
  background-size: 100% 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  .login-box {
    width: 500px;
    height: 400px;
    background-color: #fff;
    padding: 20px;
    h1 {
      text-align: center;
    }
    .login-btn {
      width: 100%;
    }
  }
}
</style>
