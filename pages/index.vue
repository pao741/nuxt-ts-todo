<template>
  <v-container>
    <v-row justify="center" align="center">
      <v-col cols="12" sm="8" md="6">
        <v-text-field
          v-model="adding"
          placeholder="Write Something"
          solo
          clearable
          @keydown.enter="createTodo(adding)"
        ></v-text-field>
      </v-col>
    </v-row>
    <v-row
      justify="center"
      align="center"
      v-for="(todo, index) in todos"
      :key="todo.task"
    >
      <v-checkbox v-model="todo.completed" :label="todo.task"></v-checkbox>
      <v-icon @click="deleteTodo(index)">mdi-trash-can</v-icon>
    </v-row>
  </v-container>
</template>

<script lang="ts">
declare interface Task {
  //id: number,
  task: string;
  completed: boolean;
}

export default {
  name: "todo",
  data: () => {
    return {
      data: {},
      adding: "",
      todos: [
        {
          //"id": 1,
          task: "create todo app",
          completed: false,
        },
      ] as Task[],
    };
  },
  methods: {
    createTodo(todo: string): void {
      const newTask: Task = { task: todo, completed: false };
      this.todos.push(newTask);
      this.adding = "";
    },
    deleteTodo(key: number): void {
      if (this.todos[key].completed === true) {
        this.todos.splice(key, 1);
      }
      //   delete this.todos[key];
    },
  },
};
</script>

<style></style>
