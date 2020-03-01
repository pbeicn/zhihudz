<template>
  <div class="login_h1">
    <br />
    <br />
    <br />
    <br />
    <br />
    <table width="98%">
      <tr>
        <td width="35%" align="right">
          <img src="@/assets/gexinghuadingzhi.png" class="img1" />
        </td>
        <td align="left">
          <img src="@/assets/login-bb.png" class="img1" />
        </td>
      </tr>
    </table>

    <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <div class="box">
      <div>
        <mt-field placeholder="手机号码" v-model="username"></mt-field>
        <br />
        <mt-field
          placeholder="登录密码"
          type="password"
          v-modal="password"
        ></mt-field>
      </div>
    </div>
    <br />
    <br />
    <div class="box1">
      <div>
        <router-link to="/reg" style="color: #108EE9">注册新用户</router-link>
      </div>
      <div>找回密码</div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      username: "",
      password: "",
      aborder: true,
      logininfo: {
        grant_type: "password",
        client_id: "practice",
        password: ""
      }
    };
  },
  methods: {
    onSubmit() {
      sessionStorage.clear();
      alert(this.username);
      alert(this.password);
      this.$ajax
        .post("/oauth/token", this.$qs.stringify(this.logininfo))
        .then(res => {
          window.console.log(res);
          // sessionStorage.setItem(
          //   "access_token",
          //   "bearer" + res.data.access_token
          // );
          // this.$router.push("/main");
        })
        .catch(res => {
          window.console.log(res);
        });
    }
  }
};
</script>
<style lang="less" scoped>
input::-webkit-input-placeholder {
  color: #d9d9d9;
  font-size: 36px;
}
.bg {
  background: rgb(153, 243, 7);
}
.login_input {
  height: 100px;
  font-size: 36px;
}
.login_h1 {
  background: rgba(255, 255, 255, 1);
}

.box1 {
  justify-content: center;
}
.img1 {
  height: 190px;
}
.box {
  display: flex;
  justify-content: center;
}
.box div {
  width: 700px;
  text-align: center;
}
.input1 {
  height: 120px;
  font-size: 28px;
}
.input2 {
  font-size: 28px;
  height: 130px;
}
.input3 {
  font-size: 15vw !important;
  height: 7vh;
}
.input4 {
  font-size: 30px;
  height: 80px;
  border: 1px solid rgb(246, 248, 242);
}
.input5 {
  font-size: 30px;
  height: 80px;
  border-left: 1px solid rgb(246, 248, 242);
  border-right: 1px solid rgb(246, 248, 242);
  border-bottom: 1px solid rgb(246, 248, 242);
}
.box1 {
  display: flex;
  justify-content: center;
  div {
    width: 700px;
    text-align: center;
    color: rgb(85, 132, 226);
  }
}
</style>
