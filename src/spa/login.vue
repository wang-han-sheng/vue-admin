
<template>
  <div class="login">
    <div class="login_box">
      <div class="logo">
        <img src="../assets/logo.png" alt />
      </div>
      <div class="login_form">
        <el-form :model="loginFormData" :rules="rules" ref="loginFormData">
          <el-form-item prop="username">
            <el-input v-model="loginFormData.username" prefix-icon="el-icon-s-custom"></el-input>
          </el-form-item>
          <el-form-item prop="password">
            <el-input v-model="loginFormData.password" type="password" prefix-icon="el-icon-lock"></el-input>
          </el-form-item>
          <el-form-item>
            <el-button type="primary" @click="submitForm('loginFormData')" :loading="loading">提交</el-button>
            <el-button @click="resetForm('loginFormData')">重置</el-button>
          </el-form-item>
        </el-form>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      loading: false,
      loginFormData: {
        username: 'admin',
        password: ''
      },
      rules: {
        username: [
          { required: true, message: '请输入用户名', trigger: 'blur' },
          { min: 2, max: 10, message: '至少输入2个字符' }
        ],
        password: [{ required: true, message: '请输入密码' }]
      }
    }
  },
  methods: {
    submitForm(login_formData) {
      this.$message({ message: '登录成功', type: 'success' })
      console.log(typeof this.loginFormData)
    },
    resetForm(login_form) {
      this.$refs[login_form].resetFields()
      this.$message({ message: '重置成功', type: 'warning' })
    }
  }
}
</script>

<style lang="scss" scoped>
.login {
  width: 100%;
  height: 100%;
  background-color: #2b4b6b;
  .login_box {
    width: 400px;
    height: 400px;
    position: absolute;
    border: 1px solid #fff;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    background-color: #fff;
    .logo {
      width: 120px;
      height: 120px;
      border-radius: 50%;
      border: 1px solid #ddd;
      position: absolute;
      left: 140px;
      top: -60px;
      background-color: #2b4b6b;
      box-shadow: 0 0 10px #fff;
      img {
        width: 100%;
        height: 100%;
        border-radius: 50%;
      }
    }
  }
}

.login_form {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
</style>