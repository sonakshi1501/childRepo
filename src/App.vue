<template>
  <v-app>
    <v-main>
      <v-container>
        <v-row>
          <v-col>
            <h2>Detailed Calories in the deserts</h2>
            <p>Props received and the value is: {{title}}</p>
          </v-col>
        </v-row>
        <v-row>
          <v-col>
            <v-text-field
              type="text"
              label="Enter Name"
              placeholder="Enter name"
              v-model="name"
              outlined
            ></v-text-field>
          </v-col>
          <v-col>
            <v-text-field
              type="number"
              label="Enter Calories"
              placeholder="Enter calories"
              v-model="calories"
              outlined
            ></v-text-field>
          </v-col>
          <v-col>
            <v-btn flat color="secondary" @click="addBtn"> Add Data </v-btn>
          </v-col>
        </v-row>
        <v-row>
          <v-col>
            <v-table>
              <template v-slot:default>
                <thead>
                  <tr>
                    <th class="text-left">Name</th>
                    <th class="text-left">Calories</th>
                    <th class="text-left">Actions</th>
                  </tr>
                </thead>
                <tbody>
                  <tr v-for="(item,index) in desserts" :key="item.name">
                    <td>{{ item.name }}</td>
                    <td>{{ item.calories }}</td>
                    <td><v-btn @click="deleteData(index)" color="error" plain size="small"> Delete </v-btn></td>
                  </tr>
                </tbody>
              </template>
            </v-table>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      name: "",
      calories: "",
      desserts: [
        {
          name: "Frozen Yogurt",
          calories: 159,
        },
        {
          name: "Ice cream sandwich",
          calories: 237,
        },
        {
          name: "Eclair",
          calories: 262,
        },
        {
          name: "Cupcake",
          calories: 305,
        },
        {
          name: "Gingerbread",
          calories: 356,
        },
        {
          name: "Jelly bean",
          calories: 375,
        },
        {
          name: "Lollipop",
          calories: 392,
        },
        {
          name: "Honeycomb",
          calories: 408,
        },
        {
          name: "Donut",
          calories: 452,
        },
        {
          name: "KitKat",
          calories: 518,
        },
      ],
    };
  },
  props:['title'],
  methods: {
    addBtn() {
      if (this.name.length > 0) {
        let holddata = {
          name: this.name,
          calories: this.calories,
        };
        this.desserts.unshift(holddata);
      } else {
        alert("No data found");
      }
    },
    deleteData(index){
      if(confirm("Are you sure")){
        this.desserts.splice(index,1)
      }
    }
  },
};
</script>
