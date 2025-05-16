<template>
  <input v-model="dis" class="input" type="text" placeholder="Введите заголовк:">
  <input v-model="task" class="input" type="text" placeholder="Что вы планируете сделать?">
  <div class="buttons">
    <button @click="addTask" type="button" class="add">Добавить</button>
    <button @click="delTask" type="button" class="del">Удалить</button>
  </div>
  <p class="p" v-for="(i,j) in tasks":key='j'>
    <span class="counter">{{`Задача №${j+1}` }}</span>
    <span class="dis">{{ i.dis }}</span>
    <span class="task">{{ i.task }}</span>
  </p>
</template>
<script>
export default{
  data(){
    return{
    tasks:[],
    task:"",
    dis:""
    }
  },
  methods:{
    addTask(){
      if(this.task=="" ||this.dis=="")return false;
      const q={
        task:this.task,
        dis:this.dis
      }
      this.tasks.push(q);
      this.task="";
      this.dis="";
    },
    delTask(){
      this.tasks.pop();
    }
  }
}
</script>
<style scoped>
.input{
  width:250px;
  height:50px;
  background-color:pink;
  color:black;
  margin:20px 20px 0px 20px;
}
.add{
  width:90px;
  height:30px;
  background-color:rgb(11, 175, 11);
  border-radius:10px;
  display:block;
  margin:20px 5px 20px 20px;
}
.del{
  width:90px;
  height:30px;
  background-color:rgb(175, 11, 11);
  border-radius:10px;
  margin:20px 20px 20px 10px;
}
.buttons{
  display:flex;
}
.p{
  display:block;
  width:290px;
  height:75px;
  background-color:pink;
  margin:0px 20px 20px 20px;
  border:2px solid black;
  word-wrap:break-word;
}
.task{
  display:block;
}
.dis{
  margin-left:50px;
}
</style>