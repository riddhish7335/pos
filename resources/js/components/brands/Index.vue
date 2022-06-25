<template>
<div >
    <div class="row">
            <router-link :to="{ name: 'store-brand'}" class="btn btn-primary">Add Brand</router-link>
        </div>
    <br />
    <br />
    <div class="row">
            <div class="col-lg-12 mb-4">
              <!-- Simple Tables -->
              <div class="card">
                <div class="card-header py-3 d-flex flex-row align-items-center justify-content-between">
                  <h6 class="m-0 font-weight-bold text-primary">Brand List</h6>
                </div>
                <div class="table-responsive">
                  <table class="table align-items-center table-flush">
                    <thead class="thead-light">
                      <tr>
                        <!-- <th>Id</th> -->
                        <th>Brand Name</th>
                        <th>Action</th>
                      </tr>
                    </thead>
                    <tbody>
                      <tr v-for="brand in filtersearch" :key="brand.id">
                        <!-- <td>{{ supplier.id }}</td> -->
                        <td>{{ brand.name }}</td>
                        <td></td>
                      </tr>
                    </tbody>
                  </table>
                </div>
                <!-- <div class="card-footer"></div> -->
              </div>
            </div>
          </div>
        
</div>
</template>
<script>

export default{
     data(){
        return{
            brands:[],
            searchTerm: ''
        }
    },
    computed: {
      filtersearch(){
        return this.brands.filter(brand => {
          return brand.name.match(this.searchTerm)
        })
      }
    },
    methods:{
        getAllBrands(){
            axios.get(globalURL+'/api/brand/')
            .then(({data}) => (this.brands = data))
            .catch()
        }
    },created(){
        this.getAllBrands();
        
    },
}
</script>