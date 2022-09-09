<template>
    <div class="d-flex justify-content-center align-items-start flex-wrap">
        
        <div class="card m-3 mw-250px" v-for="char in dataChar.results">
            <img class="card-img-top" :src="char.image" alt="Card image cap">
            <div class="card-body">
                <h2>
                    {{char.name}}
                </h2>
                <p>
                    {{char.status}}
                </p>
            </div>
        </div>

    </div>
</template>

<script>
    import axios from 'axios'

    export default {
        data: () => {
            return {
                dataChar: []
            }
        },
        mounted() {
            console.log('Component mounted.')
            this.start()
        },
        methods: {
            async start() 
            {
                axios
                .get("https://rickandmortyapi.com/api/character")
                .then((res) => {
                    console.log(res.data)
                    this.dataChar = res.data;
                })
                .catch((error) => {
                    console.log(error);
                });
            }
        }
    }
</script>

<style>
    .mw-100px{
        max-width: 100px;
    }

    .mw-250px{
        max-width: 250px;
    }
</style>