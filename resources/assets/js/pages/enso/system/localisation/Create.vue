<template>

    <div class="container">
        <div class="columns is-centered">
            <div class="column is-three-quarters">
                <vue-form :data="form"
                    class="box animated fadeIn"
                    v-if="initialised">
                    <template slot="flag" slot-scope="props">
                        <input class="input"
                            type="text"
                            disabled>
                    </template>
                </vue-form>
            </div>
        </div>
    </div>

</template>

<script>

import VueForm from '../../../../components/enso/vueforms/VueForm.vue';

export default {
    components: { VueForm },

    data() {
        return {
            initialised: false,
            form: {},
        };
    },

    created() {
        axios.get(route(this.$route.name, null, false)).then((response) => {
            this.form = response.data.form;
            this.initialised = true;
        }).catch(error => this.handleError(error));
    },
};

</script>
