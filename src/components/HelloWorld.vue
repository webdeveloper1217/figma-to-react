<template>
  <div class="hello">
    <button v-on:click="updateMemberData()">Test AXIOS function</button>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "AxiosTest",
  props: {
    msg: String,
  },

  methods: {
    updateMemberData: function() {
      var data = {
        Affiliations: "Stony Brook",
        DBID: "SB        ",
        Department: "Biochemistry & Cell Biology",
        Email: "Michael.Airola@stonybrook.edu",
        First_Name: "Michael",
        ID: 33,
        Last_Name: "Airola",
        MI: "V",
        Membership_Type: "Associate Research",
        ProgramName: "Cancer Lipids and Metabolism",
        Program_Code: "CLM",
        Status: "Active",
        Year_End: 3000,
        Year_Start: 2015,
      };
      axios
        .post("http://admin-api.org/api/saveJSON", data, {
          headers: {
            "Access-Control-Allow-Origin": "POST",
          },
        })
        .then((data) => {
          console.log("{}{}{", data);
        })
        .catch((error) => {
          console.log("{}{}{}000000000", error);
        });
      // var config = {
      //   method: 'post',
      //   url: 'http://admin-api.org/api/saveJSON',
      //   headers: {
      //     'Content-Type': 'application/json'
      //   },
      //   data : data
      // };

      // axios(config)
      // .then(function (response) {
      //   console.log(JSON.stringify(response.data));
      // })
      // .catch(function (error) {
      //   console.log(error);
      // });
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
