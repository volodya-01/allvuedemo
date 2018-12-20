<template>
  <div class="hello">
    <p>
      {{hello}}&nbsp;&nbsp;&nbsp;
    {{10*666-88-77+44}}&nbsp;&nbsp;&nbsp;
    {{"哈哈"}}&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
   {{9}}
    </p>
   <p v-html="hello"></p>
   <p v-text="hello"></p>
   <p v-bind:class="ha">哈哈哈</p>
   <p v-bind:title="ts">提示</p>
   <p><input type="text" v-bind:placeholder="sr"></p>
   <p v-bind:id="box">改变颜色和字体大小</p>
   <p><button  v-on:click="add11">box1的颜色</button>
   <button  v-on:click="add12">box2的颜色</button></p>
<p>{{mes.split('').reverse().join('')}}</p>
  <div>
    <p v-if="show">我是if为true是看到的</p>
    <p v-else>我是if为false看到的</p>
  </div>

  <p v-if="vif">我是v-if</p>
  

  <div class="list">
    <ul>
      <li v-for="(name,index) in names" :key="index">{{name}}--{{index}}</li>
    </ul>
    <ul class="user">
      <li v-for="(item,index) in user" :key="index">
       <span> {{item.name}}</span>
        <span>{{item.age}}</span>
      </li>
    </ul>
<p>{{num}}</p>
    <button v-on:click="num+=1">按钮</button>
    <button v-on:click="add">按钮1</button>
  <div class="showb"> <p v-show="vsw">我是v-show</p></div>
     <p>
         <button v-on:click="add1">按钮2</button> 
     </p>
  </div>

  <div class="event">
    <div>下面是names的循环列表</div>
    <ul>
      <li v-on:click.once="getItemInfo(index,$event)" v-for="(name,index) in names" :key="index">
        <span>{{index+1}}</span>
        <span>、</span>
        <span>{{name}}</span>
        </li>
    </ul>
    <input type="text" v-on:keyup.enter="keyevent" placeholder="enter修饰符：仅可监听enter事件">
    <input type="text" v-on:keyup="keyevent" placeholder="可监听所有按键事件">
    <button @click="getodd">我想要奇数</button>
  </div>


  <p>{{mes.split('').reverse().join('')}}</p>
  <p>{{mes.split('').reverse().join('')}}</p>
  <p>{{mesreg}}</p>
  <p>{{mesreg}}</p>
  <p>{{mesreg}}</p>
  <p> methodsmesreg():{{ methodsmesreg()}}</p>
  <form action="">
   <p> 姓名：<input type="text" v-model="xm"> <span>{{xm}}</span></p>
   <p> 账号：<input type="number" v-model.trim="zh"> <span>{{zh}}</span></p>
    <p>密码：<input type="password" v-model.trim="mm"> <span>{{mm}}</span></p>
  </form>

  <div v-bind:class="{active:isActive,'demo':Demo}">哈哈</div>
  <div v-bind:class="styobj">哈哈2</div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      names:['iwe','ime','ice'],
     hello:"<p>hello,VUE</p>",
     "哈哈":"哈哈",
     ha:"ha1",
     ts:"我是提示",
   sr:"已经输入别废话",
   mes:"一二三四五六七八九十百千万",
   box:"box1",
   show:false,
   vif:false,
   vsw:false,
  /*  names:["ami","awen","jack"], */
  styobj:{
    active:true,
    'demo':true
    },
  isActive:true,
  Demo:true,
  xm:"",
  zh:"",
  mm:"",
   num:1,
   nums:[1,2,3,4,5,6,7,8,9,11,21,34,1,23,44,667,2,434,21],
   user:[
     {
     id:0,
     name:"jack",
     age:18     
   },
   {
     id:1,
     name:"voliu",
     age:23     
   },
   {
     id:2,
     name:"jaqeqek",
     age:24     
   },
   ]
    }
  },
  computed:{
    mesreg(){
     return  this.mes.split('').reverse().join('')
    }
  },
  watch:{
    xm:function(data){
      if(data==2){
        console.log("你妹的")
      }
    },
    zh:function(data){
      console.log(data)
    },
    mm:function(data){
      console.log(data)
    }
  },
  methods:{
    methodsmesreg(){
     return  this.mes.split('').reverse().join('')
    },
    add(){
      this.num+=1
    },
    add1(){
      this.vsw=!this.vsw
    },
    add11(){
      this.box="box1"
      
    },
     add12(){
      this.box="box2"
      console.log(this)
    },
    getItemInfo(dat,event){
      console.log(this.names[dat])
console.log(dat)
console.log(event)
    },
    keyevent(event){
    
console.log(event)
    },
    getodd(){
      this.nums.filter(function(num){
        if(num%2!==0){
          console.log('$'+num)
          document.write('$'+num+<br/>)
          return num
        }
return num%2!==0;
      })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.hello{
  font-size: 36px;
  color: brown
}
.active{
  color: chartreuse;
}
#box1{
   font-size: 76px;
  color:#548ff6;
  width: 0684px;
  height: 1px;
  border-bottom: 3px #538ff6 solid;
  line-height: 76px;
  align-content: center;
}
#box2{
   font-size: 76px;
  color:black;
  width: 0684px;
  height: 120px;
  line-height: 76px;
  align-content: center;
}
.user{
  list-style: none;
  color: chocolate;
  font-size: 36px;
}
.showb{
  width: 200px;
  height: 200px;
  border: 2px gray solid;
  margin:auto auto
}
.showb>p{
  line-height: 100px;
  text-align: center;
}
</style>
