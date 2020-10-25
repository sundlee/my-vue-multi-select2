<template>
  <div>
    <vue-multi-select
      ref="multiSelect"
      v-model="values"
      search
      :options="options"
      :filters="filters"
      :btnLabel="btnLabel"
      @open="open"
      @close="close"
      :selectOptions="data"
    >
      <template v-slot:option="{option}">
        <input type="checkbox" :checked="option.selected"/>
        <span class="name">{{option.name}}</span><span>{{option.length}}</span>
      </template>
    </vue-multi-select>
    <button @click="openManually">
      Open manually
    </button>
    <div>{{values}}</div>
  </div>
</template>

<script>
import vueMultiSelect from 'vue-multi-select';
import 'vue-multi-select/dist/lib/vue-multi-select.css';

export default {
  name: 'MultiSelect',
  data() {
    return {
      btnLabel: values => `API 리소스 선택 (${values.length})`,
      name: 'first group',
      values: [],
      data: [
        { name: '0', length: '1000' },
        { name: '2', length: '1000' },
        { name: '3', length: '1000' },
        { name: '8', length: '1000' },
        { name: '9', length: '1000' },
        { name: '11', length: '1000' },
        { name: '13', length: '1000' },
        { name: '14', length: '1000' },
        { name: '15', length: '1000' },
        { name: '18', length: '1000' },
      ],
      filters: [{
        nameAll: 'Select all',
        nameNotAll: 'Deselect all',
        func() {
          return true;
        },
      }],
      options: {
        multi: true,
        groups: false,
        cssSelected: option => (option.selected ? { 'background-color': '#ff6a6a' } : ''),
        popoverClass: "#41b883",
      },
    };
  },
  methods: {
    openManually() {
      this.$refs.multiSelect.openMultiSelect();
    },
    open() {
      console.log('open');
    },
    close() {
      console.log('close');
    },
  },
  components: {
    vueMultiSelect,
  },
};
</script>

<style>
.name {
  color: red;
}
</style>