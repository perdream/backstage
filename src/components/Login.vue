<template>
  <div class="container">
    <div class="container2">
      <el-form
        :model="ruleForm"
        status-icon
        :rules="rules"
        ref="ruleForm"
        label-width="100px"
        class="demo-ruleForm"
      >
        <el-form-item label="用户名" prop="userName">
          <el-input v-model="ruleForm.userName" prefix-icon="el-icon-user-solid"></el-input>
        </el-form-item>
        <el-form-item label="密码" prop="passWord">
          <el-input type="password" v-model="ruleForm.passWord" autocomplete="off" prefix-icon="el-icon-edit"></el-input>
        </el-form-item>
        <el-form-item>
          <el-button type="primary" @click="submitForm('ruleForm')">提交</el-button>
          <el-button @click="resetForm('ruleForm')">重置</el-button>
        </el-form-item>
      </el-form>
    </div>
  </div>
</template>

<script>
/* eslint-disable */
export default {
  name: "Login",
  data() {
    var checkUserName = (rule, value, callback) => {
      if (!value) {
        return callback(new Error("用户名不能为空"));
      }
    };
    var validatePass = (rule, value, callback) => {
      if (value === "") {
        callback(new Error("请输入密码"));
      }
    };
    return {
      ruleForm: {
        userName: "",
        passWord: "",
      },
      rules: {
        userName: [{ validator: checkUserName, trigger: "blur" }],
        passWord: [{ validator: validatePass, trigger: "blur" }]
      }
    };
  },
  methods: {
    submitForm(formName) {
      this.$refs[formName].validate(valid => {
        if (valid) {
          alert("submit!");
        } else {
          console.log("error submit!!");
          return false;
        }
      });
    },
    resetForm(formName) {
      this.$refs[formName].resetFields();
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: olivedrab;
}
.container2 {
  height: 400px;
  width: 500px;
  margin: 0 auto;
  margin-top: 15%;
}
</style>
