<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-lg-12">
        <h2 class="text-center my-4">BUKU</h2>
        <div class="my-3">
          <form @submit.prevent="getBooks">
            <input type="search" class="form-control rounded-5" placeholder="Mau baca apa hari ini?">
          </form>
        </div>
        <div class="my-3 text-muted">menampilkan 4 dari 125</div>
        <div class="row justify-content-evenly">
          <div class="col-lg-2">
            <div v-for="(book,i) in books" :key="i" class="col-lg-2"></div>
            <div class="card mb-3">
              <div class="card-body">
                <img src="~/assets/img/cover1.jpg" class="cover" alt="cover 1">
              </div>
            </div>
          </div>
          <div class="col-lg-2">
            <div class="card mb-3">
              <div class="card-body">
                <img src="~/assets/img/cover2.jpg" class="cover" alt="cover2">
              </div>
            </div>
          </div>
          <div class="col-lg-2">
            <div class="card mb-3">
              <div class="card-body">
                <img src="~/assets/img/cover3.jpg" class="cover" alt="cover3">
              </div>
            </div>
          </div>
          <div class="col-lg-2">
            <div class="card mb-3">
              <div class="card-body">
                <img src="~/assets/img/cover4.jpg" class="cover" alt="cover4">
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <nuxt-link to="/">
    <button type="button" class="btn btn-primary">KEMBALI</button></nuxt-link>
  </div>
</template>

<script>
const keyword = ref ('')
const supabase = useSupabaseClient()
const books = ref([])
const getBooks = async () => {
  const { date, error } =await supabase.from('buku').select(`*, kategori(*)`)
  .ilike('judul','%${keyword.value}%')
  if(data) books.value = data
}

onMounted(() => {
  getBooks()
})
</script>

<style scoped>
.card-body {
  width: 100%;
  height: 20em;
  padding: 0;
}
.cover {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: 0 30;
}
</style>