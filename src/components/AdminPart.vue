<template>
    <div class="lists-row">
        <draggable class="list" :list="list1" group="people" @change="log" itemKey="name">
            <template #item="{ element, index }">
                <div class="list__item">{{ element.name }} {{ index }}</div>
            </template>
        </draggable>

        <draggable class="list" :list="list2" group="people" @change="log" itemKey="name">
            <template #item="{ element, index }">
                <div class="list__item">{{ element.name }} {{ index }}</div>
            </template>
        </draggable>
    </div>
</template>
<script setup lang="ts">
import draggable from 'vuedraggable';
import { reactive } from 'vue';
const list1 = reactive(
    [
        { name: "Анатоль", id: 1 },
        { name: "Василий", id: 2 },
        { name: "Перчик", id: 3 },
        { name: "Белуга", id: 4 }
    ]
)
const list2 = reactive(
    [
        { name: "Алексей", id: 7 },
        { name: "Гриша", id: 562 },
        { name: "Вова", id: 653 },
        { name: "Кеша", id: 64 }
    ]
)
const add = () => {
    list1.push({ name: "Juan" });
}
const replace = () => {
    this.list = [{ name: "Edgard" }];
}
const clone = () => {
    return {
        name: el.name + " cloned"
    }
}
const log = (evt) => {
    window.console.log(evt);
}
</script>
<style lang="sass">
.lists-row 
    display: flex
    gap : 10px
.list
    display: grid
    flex-direction: column 
    width: 300px
    align-items: center 
    border-radius: 0.2rem  
    color : black 
    gap : 1px
    border: 1px solid #b5b5b5
    

    > * 
        font-size : 16px

    background-color: #b5b5b5
    
    &__item
        width : 100% 
        padding : 0.5rem 0
        background-color : white
        text-align: center
    
    &__button
        width : 100% 
        padding : 0.5rem 0
        background-color : #b5b5b5
        color : white
        text-align: center
        outline : unset
        border : unset
        

</style>