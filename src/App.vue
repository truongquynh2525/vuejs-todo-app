<script setup lang="ts">
import { ref } from 'vue'

type TodoItem = {
  Name: string | undefined
}

const input = ref<TodoItem>({ Name: '' }) // Initialize input with an empty TodoItem
const todoList = ref<TodoItem[]>([]) // Specify the type for todoList

const handleOnClick = () => {
  todoList.value.push({ Name: input.value.Name }) // Access the Name property directly without optional chaining
  input.value.Name = ''
}

const handleOnRemove = (name?: string) => {
  // remove the name from todo list
  todoList.value = todoList.value.filter((todo) => todo.Name !== name)
}
</script>

<template>
  <main>
    <!-- create an input and a button -->
    <input type="text" v-model="input.Name" />
    <!-- Access the Name property directly without optional chaining -->
    <button @click="handleOnClick">Add new todo</button>
    <!-- Remove parentheses from handleOnClick -->
    <!-- render todoList -->
    <div v-for="todo in todoList" :key="todo.Name">
      <!-- Specify a unique key for the v-for loop -->
      <p>{{ todo.Name }}</p>
      <button @click="handleOnRemove(todo.Name)">Remove</button>
    </div>
  </main>
</template>

<style scoped></style>
