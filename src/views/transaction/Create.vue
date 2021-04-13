<template>
    <div class="container my-5">
        <div class="row justify-content-center">
            <div class="col-8">
                <router-link 
                :to="{name: 'transaction.index'}"
                class="btn btn-primary btn-sm rounded shadow mb-3"
                >Back</router-link>

                <div class="card rounded shadow">
                    <div class="card-header">
                        Create Transaction 
                    </div>

                    <div class="card-body">
                        <form>
                            <div class="mb-3">
                                <label for="" class="form-label">Title</label>
                                <input type="text" class="form-control">

                                <div class="text-danger">
                                    Validation message
                                </div>
                            </div>

                            <div class="mb-3">
                                <label for="" class="form-label">Amount</label>
                                <input type="number" class="form-control">

                                <div class="text-danger">
                                    Validation message
                                </div>
                            </div>

                            <div class="mb-3">
                                <label for="" class="form-label">Time</label>
                                <input type="text" class="form-control" placeholder="yyyy-mm-dd hh:mm:ss">

                                <div class="text-danger">
                                    Validation message
                                </div>
                            </div>

                            <div class="mb-3">
                                <label for="" class="form-label">Type</label>
                                <select id="" class="form-select">
                                    <option value="expense">Expense</option>
                                    <option value="revenue">Revenue</option>
                                </select>

                                <div class="text-danger">
                                    Validation message
                                </div>
                            </div>

                            <button class="btn btn-outline-primary">Submit</button>
                        </form>
                    </div>
                </div>

            </div>
        </div>
    </div>

</template>

<script>
import { reactive, ref} from 'vue'
import { useRouter } from 'vue-router'
import axios from 'axios'
export default {
    setup(){
        // data binding
        const transaction = reactive({
            title: '',
            amount: '',
            time: '',
            type: '',

        });

        const validation = ref([]);

        const router = useRouter();

        function store(){
            axios.post(
                'http://127.0.0.1:8000/api/transaction',
                transaction
            )

            .then(()=>{
                router.push({
                    name: transaction
                })
            }).catch((err)=>{

            });
        }

    }
}
</script>