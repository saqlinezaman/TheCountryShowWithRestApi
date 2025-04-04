<script setup>
import axios from 'axios';
import { ref } from 'vue';
const ListData=ref([])  
CallCountryListData()
async function CallCountryListData(){
  let res=await axios.get('https://countrylist.teamrabbil.com/api/country-list')
  ListData.value=res.data
}
</script>
<template>
  <!-- table start -->
  <div class="p-4">
  <div class="overflow-x-auto">
    <table class="min-w-full border border-gray-200 rounded-lg overflow-hidden shadow-md">
      <thead class="bg-gray-100">
        <tr>
          <th class="px-6 py-3 text-left text-sm font-medium text-gray-700">Flag</th>
          <th class="px-6 py-3 text-left text-sm font-medium text-gray-700">Country Name</th>
          <th class="px-6 py-3 text-left text-sm font-medium text-gray-700">Capital</th>
          <th class="px-6 py-3 text-left text-sm font-medium text-gray-700">Description</th>
        </tr>
      </thead>
      <tbody class="bg-white divide-y divide-gray-200">
        <tr v-for="(item) in ListData">
          <td class="px-6 py-4">
            <img :src="item['flag']" alt="flag" class="w-12 h-12 rounded-full">
          </td>
          <td class="px-6 py-4 text-sm text-gray-800">{{ item['name'] }}</td>
          <td class="px-6 py-4 text-sm text-gray-600">{{ item['capital'] }}</td>
          <td class="px-6 py-4 text-sm text-gray-600">{{ item['short_description'] }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</div>

</template>
<style>
</style>