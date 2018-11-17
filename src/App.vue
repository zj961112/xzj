<template>
    <div>
        <header class="site-header jumbotron">
            <div class="container">
                <div class="row">
                    <div class="col-xs-12">
                        <h1>请发表对Vue的评论</h1>
                    </div>
                </div>
            </div>
        </header>
        <div class="container">
            <Add :addComment="addComment"/>
            <!--将数据comments传给List组件-->
            <List :comments="comments" :deleteComment="deleteComment"/>
        </div>
    </div>
</template>

<script>
    import Add from './components/Add.vue'
    import List from './components/List.vue'
    export default{
        //因为初始化数据是某些组件需要用到所以放到组件的父级组件里
        data(){
            return{
                comments:[   //数据在哪个组件，更新数据的行为（方法）就应该定义在哪个组件
                    {
                        name:'Bob',
                        content:'Vue 还不错'
                    },
                    {
                        name:'Cat',
                        content:'Vue so easy'
                    },
                    {
                        name:'David',
                        content:'Vue so so'
                    }
                ]
            }
        },
        //映射成标签
        components:{
            Add,
            List
        },
        methods:{
            //添加评论
            addComment(comment){
                this.comments.unshift(comment) //unshift() 方法可向数组的开头添加一个或更多元素，并返回新的长度。
            },
            //删除指定下标的评论
            deleteComment(index){
                this.comments.splice(index,1)
            }
        }
    }
</script>

<style>

</style>