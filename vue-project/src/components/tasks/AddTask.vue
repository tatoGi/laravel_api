<template>
    <div class="relative">
        <input
            type="text"
            class="form-control form-control-lg padding-right-lg"
            placeholder="+ Add new task. Press enter to save."
            @keydown.enter="addNewTask"
        />
    </div>
</template>

<script setup>
import { reactive, defineEmits } from "vue";

const AddTask = reactive({
    name: '',
    is_completed: false
});

const emit = defineEmits(['added']);

const addNewTask = async (event) => {
    if (event.target.value.trim()) {
        AddTask.name = event.target.value;
        event.target.value = "";
        emit('added', AddTask);
    }
};
</script>
