<template>
  <div id="app">
    <h1>{{`基于Element-UI组件改造的树形选择器`}}</h1>
    <!-- 调用树形下拉框组件 -->
    <SelectTree 
      :props="props"
      :options="list"
      :value="valueId"
      :clearable="isClearable"
      :accordion="isAccordion"
      @getValue="getValue($event)"/>
  </div>
</template>

<script>
import SelectTree from "./components/treeSelect.vue";

export default {
  name: "app",
  components: {
    SelectTree
  },
  data() {
    return { 
      isClearable:true,     // 可清空（可选）
      isAccordion:true,     // 可收起（可选）
      valueId:5,            // 初始ID（可选）
      props:{               // 配置项（必选）
        value: 'id',
        label: 'title',
        children: 'children',
        // disabled:true
      },
      // 选项列表（必选）
      list:[
        {
          id:1,
          title:'Vue.js',
          parentId:0
        },{
          id:2,
          title:'Element-UI',
          parentId:0,
          disabled:true,
          children:[
            {
              id:4,
              title:'el-select',
              parentId:2,
              children:[
                {
                  id:5,
                  title:'el-tree',
                  parentId:4
                }
              ]
            }
          ]
        },{
          id:3,
          title:'JavaScript',
          parentId:0,
          children:[
            {
              id:6,
              title:'选择器',
              parentId:3,
              children:[
                {
                  id:7,
                  title:'树形选择器',
                  parentId:6  
                }
              ]
            }
          ]
        }
      ]
    };
  },
  methods:{
    // 取值
    getValue(value){
      this.valueId = value
      console.log(this.valueId);
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
