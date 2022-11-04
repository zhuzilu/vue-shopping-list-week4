<template>
  <h1>SHOPPING LIST</h1>
    <div id="shop-wrap">
      <!-- (A) ADD NEW ITEM -->
      <div id="shop-form">
        <input 
          type="text" 
          id="shop-item" 
          placeholder="Item Name" 
          v-model="text"
          required
        />
        <button
          @click="addItem"
          type="submit" 
          id="shop-add"> Add 
        </button>
      </div>

      <!-- (B) SHOPPING LIST -->
      <div id="shop-list">
        <div v-for="(item, index) in list" :key="item" class="item-row">
          <div class="item-name">{{item}}</div>
          <button class="item-del" @click="deleteItem(index)">Delete</button>
        </div>
      </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import ShoppingList from './components/ShoppingList.vue';

export default defineComponent({
  name: 'App',
  components: {
    ShoppingList
  },
  data: function() {
    return {
      list: ['Potatoes 🥔','Corn 🌽', 'Soy milk 🥛', 'Carrots 🥕'],
      text: '',
      index: null,
    }
  },
  methods: {
    addItem() {
      this.list.push(this.text);
    },
    deleteItem(index: number) {
      console.log(index)
      this.list.splice(index, 1);
    }
  }
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
/* (A) SHARED */
#shop-wrap, #shop-wrap > * { box-sizing: border-box; }
#shop-wrap input {
  padding: 10px;
  border: 0;
}
#shop-wrap button {
  cursor: pointer;
  color: #fff;
  background: #5a75d6;
  padding: 10px;
  border: rgb(218, 213, 213) 1px solid;
}

#shop-form, .item-row {
  display: flex;
  align-items: center;
}
#shop-item, .item-name { flex-grow: 1; }

/* (B) WRAPPER */
#shop-wrap {
  max-width: 500px;
  padding: 15px;
  background: #f2f2f2;
  border: 2px solid #eee;
}

/* (C) SHOPPING LIST */
.item-row { margin-top: 10px; }
.item-name {
  padding: 5px;
  background: #fff;
}
.item-name.item-got { background: #f5fffa; }
.item-name.item-got:before {
  content: "\02713";
  margin-right: 5px;
  font-weight: bold;
  color: #00d036;
}
.item-del { background: #de1919 !important; }

/* [DOES NOT MATTER] */
* { font-family: arial, sans-serif; }

</style>
