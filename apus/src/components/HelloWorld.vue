<script>
export default {
  data: function () {
    return {
      items: null
    }
  },
  methods: {
    fetchData: function () {
      let self = this
      const myRequest = new Request('https://api.sampleapis.com/coffee/hot')

      fetch(myRequest)
          .then((response) => {
            return response.json()
          })
          .then((data) => {
           // debugger;
            self.items = data
            console.log(self.items)
          }).catch(error => {
        console.log(error);
      });
    }
  },

  mounted() {
    this.fetchData()
  },
  props: ['msg'],
  setup(props) {
    // setup() receives props as the first argument.
    console.log(props.msg)
  }
}
</script>
<template>
  <div class="greetings">
    <h1 class="green">{{ msg }}</h1>
    <ul>
      <li v-for="item in items">
        {{ item.title }} : {{ item.description }}
      </li>
    </ul>

  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>
