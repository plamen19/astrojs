<template>

       <div class="container">

              <p v-if="cargando" class="text-muted text-center mt-4">Cargando datos...</p>
              
              <template v-else>

                     <button class="btn btn-sm btn-primary mt-2" @click="obtenerUsuarios">Refrescar</button>
                     <div class="table-responsive">

                            <table class="table">

                                   <thead>

                                          <tr>

                                                 <th>Name</th>
                                                 <th>Username</th>
                                                 <th>Email</th>
                                                 <th>Phone</th>
                                                 <th>Website</th>

                                          </tr>

                                   </thead>

                                   <tbody>

                                          <tr v-for="(user, index) in usuarios" :key="index">

                                                 <td>{{ user?.name }}</td>
                                                 <td>{{ user?.username }}</td>
                                                 <td>{{ user?.email }}</td>
                                                 <td>{{ user?.phone }}</td>
                                                 <td>{{ user?.website }}</td>

                                          </tr>

                                   </tbody>

                            </table>

                     </div>

              </template>

       </div>

</template>

<script>
import axios from 'axios';

export default {

       name: 'Usuarios',

       data(){

              return({

                     cargando: true,
                     usuarios: [], 

              })

       },

       methods: {

              obtenerUsuarios: function(){

                     this.cargando = true;
                     axios.get( 'https://jsonplaceholder.typicode.com/users' ).then( res => {

                            this.usuarios = res.data;
                            this.cargando = false;

                     } )

              }

       },

       mounted(){

              this.obtenerUsuarios();

       }

}

</script>