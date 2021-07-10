<template>
  <div class="todo">
    <div class="container">
      <div class="row d-flex justify-content-center">
        <div class="col-md-8">
          <h1>This is an Todo page</h1>

          <div class="form-group">
            <h2 class="mb-3">Todo List</h2>
            <input
              type="text"
              class="form-control"
              name="todo"
              id="todo"
              placeholder="todo"
              v-model="todo"
              @keyup.enter="addTodo"
            />
            <button class="btn btn-primary mt-3" v-on:click="addTodo()">
              Add
            </button>
          </div>

          <table class="table" v-if="todos.length > 0">
            <thead>
              <tr>
                <th scope="col">No</th>
                <th scope="col">Todo</th>
                <th scope="col">Action</th>
              </tr>
            </thead>
            <tbody v-for="(todo, index) in todos" :key="index">
              <td scope="row">{{ ++index }}</td>
              <td>{{ todo }}</td>
              <td>
                <button
                  type="button"
                  class="badge bg-danger"
                  @click="deleteTodo(index)"
                >
                  Delete
                </button>
              </td>
            </tbody>
          </table>
          <h3 class="mt-3" v-else>Todo Empty</h3>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import "bootstrap/dist/css/bootstrap.css";
export default {
  name: "Todo",
  data: function() {
    return {
      todos: [],
      todo: "",
    };
  },
  methods: {
    addTodo() {
      this.todos.push(this.todo);
      this.todo = "";
    },
    deleteTodo(index) {
      this.todos.splice(--index, 1);
    },
  },
};
</script>
