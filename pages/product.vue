<template>
<main>
  <div class="container">
    <Navigasi />
    <div>
      <div class="jumbotron">
        <product/>
      </div>
        <div class="row">
          <div class="col-md-4" v-for="item in items" :key="item.id">
            <div class="card mb-3">
              <div class="card-header">
                <img :src="item.foto" width="100%"> 
              </div>
              <div class="card-body">
                <h4>{{ item.nama }}</h4>
                <h4>Rp{{ item.harga }}</h4>
              </div>
            </div>
          </div>
        </div>
    </div>
  </div>
  <div class="container">
            <footer class="bg-dark text-center text-white">
              <div class="container p-4 pb-0">
                <section class="">
                  <form action="">
                    <div class="row d-flex justify-content-center">
                      <div class="col-auto">
                        <p class="pt-2">
                          <strong>Daftar Untuk Berlangganan</strong>
                        </p>
                      </div>
                        <div class="col-md-5 col-12">
                          <div class="form-outline form-white mb-4">
                            <input type="email" id="form5Example2" class="form-control" />
                            <label class="form-label" for="form5Example2">E-mail</label>
                          </div>
                        </div>
                        <div class="col-auto">
                          <button type="submit" class="btn btn-outline-light mb-4">
                            Langganan
                          </button>
                        </div>
                    </div>
                  </form>
                </section>
              </div>
                <div class="text-center p-3" style="background-color: rgba(0, 0, 0, 0.2);">
                  © 2022 Copyright
                  <a class="text-white" href="#">Otahi_Store</a>
                </div>
            </footer>
          </div>
</main>
</template>

<script>
export default {
  data() {
    return {
      items: '',
    }
  },
  mounted() {
    this.ambilData()
  },
  methods: {
    async ambilData() {
      const { data, error } = await this.$supabase
        .from('tb_produk')
        .select()
      if(data) this.items = data
      if(error) console.log(error)
    }
  }
}
</script>
