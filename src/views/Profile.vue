<template>
<h1>Profile</h1>
Name: {{name}} <br>
Email: {{email}}
</template>


 <script>
//  import axios from 'axios'
// // export default {
// //     mounted () {
// //     // axios
// //       .get('http://127.0.0.1:8000/api/profile')
// //       .then(response => (this.info = response))
// //   }
// //   };


// export default {
//     data: () => {
//         return { 
//             name: "Shawn",
//             items: []
//         };
//     },
//     mounted: async function () {
//         axios.get('http://127.0.0.1:8000/api/profile')
//         .then(result => {
//             // breaks reactivity
//             this.items = result.data;
//         });
//     }
// };


import axios from "axios";
export default {
  name: "HelloWorld",
  data() {
    return {
      name: '',
      email: '',
    };
  },
  mounted() {
    let token=localStorage.getItem("token");
   console.log(token);
    axios
      .get("http://127.0.0.1:8000/api/profile", {
        headers: {
          Authorization: `Bearer ${token}`,
          token: token
        }
      })
      .then(res => {
         this.name=res.data.name  
         this.email=res.data.email  
        console.log(res);
      });
  }
};


</script>