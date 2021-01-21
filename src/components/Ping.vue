<template>
  <div>
    Ping result: {{ msg }}
    <div>
      <el-button type="primary" id="apiButton" @click="this.getMessage">call test api</el-button>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'Ping',
  data () {
    return {
      msg: ''
    }
  },
  // 生命周期函数，加载页面时会先执行这个函数，从而调用 getMessage() 方法
  // created () {
  //   this.getMessage()
  // },
  methods: {
    getMessage () {
      // 使用 axios 向 flask 发送请求
      const url = 'http://127.0.0.1:5000/api/ping'
      axios.get(url)
        .then((res) => {
          this.msg = res.data
        })
        .catch((error) => {
          console.log(error)
        })
    }

  }
}
</script>

<style scoped>
#apiButton {
  margin-top: 10px;
}
</style>
