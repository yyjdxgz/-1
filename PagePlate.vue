<template>
   <div class="rd_paging" v-if="totalpage>1">
                <div class="previous_page" v-if="page_html!=1" @click.stop="prePage">
                    <img src="@/assets/productlist/icon_down.png" alt="">
                    <span>上一页</span>
                </div>
                <div class="pages" v-if="totalpage>1">
                    <template v-if="page_html<=4||totalpage<=6">
                        <span :class="page_html==1?'active':''" v-if="totalpage>=1" @click.stop="navPage(1)">1</span>
                        <span :class="page_html==2?'active':''" v-if="totalpage>=2" @click.stop="navPage(2)">2</span>
                        <span :class="page_html==3?'active':''" v-if="totalpage>=3" @click.stop="navPage(3)">3</span>
                        <span :class="page_html==4?'active':''" v-if="totalpage>=4" @click.stop="navPage(4)">4</span>
                        <span :class="page_html==5?'active':''" v-if="totalpage>=5" @click.stop="navPage(5)">5</span>
                        <span :class="page_html==6?'active':''" v-if="totalpage>=6" @click.stop="navPage(6)">6</span>
                        <span class="e" v-if="totalpage>6">...</span>
                        <span :class="page_html==totalpage?'active':''" v-if="totalpage>6" @click.stop="navPage(totalpage)">{{totalpage}}</span>
                    </template>
                    <template v-if="page_html>4&&page_html<=(totalpage-5)&&totalpage>6">
                        <span :class="page_html==1?'active':''">1</span>
                        <span class="e">...</span>
                        <span @click.stop="navPage(page_html-2)" v-if="page_html-2>0">{{page_html-2}}</span>
                        <span @click.stop="navPage(page_html-1)" v-if="page_html-1>0">{{page_html-1}}</span>
                        <span class="active">{{page_html}}</span>
                        <span @click.stop="navPage(page_html+1)">{{page_html+1}}</span>
                        <span @click.stop="navPage(page_html+2)">{{page_html+2}}</span>
                        <span class="e">...</span>
                        <span :class="page_html==totalpage?'active':''" @click.stop="navPage(totalpage)">{{totalpage}}</span>
                    </template>
                    <template v-if="totalpage>6&&page_html>(totalpage-5)&&page_html>4">
                        <span :class="page_html==1?'active':''" @click.stop="navPage(1)">1</span>
                        <span class="e">...</span>
                        <span :class="page_html==(totalpage-5)?'active':''" @click.stop="navPage(totalpage-5)" v-if="page_html-5>0">{{totalpage-5}}</span>
                        <span :class="page_html==(totalpage-4)?'active':''" @click.stop="navPage(totalpage-4)" v-if="page_html-4>0">{{totalpage-4}}</span>
                        <span :class="page_html==(totalpage-3)?'active':''" @click.stop="navPage(totalpage-3)" v-if="page_html-3>0">{{totalpage-3}}</span>
                        <span :class="page_html==(totalpage-2)?'active':''" @click.stop="navPage(totalpage-2)" v-if="page_html-2>0">{{totalpage-2}}</span>
                        <span :class="page_html==(totalpage-1)?'active':''" @click.stop="navPage(totalpage-1)" v-if="page_html-1>0">{{totalpage-1}}</span>
                        <span :class="page_html==totalpage?'active':''" @click.stop="navPage(totalpage)">{{totalpage}}</span>
                    </template>
                </div>
                <div class="next_page" @click.stop="nextPage()" v-if="page_html!=totalpage">
                    <span>下一页</span>
                    <img src="@/assets/productlist/icon_up.png" alt="">
                </div>

            </div>
</template>

<script>
export default {
  components: {},
  props: {
    totalpage:Number,
    page_html:Number

  },
  data() {
    return {
      
    };
  },
  watch: {},
  computed: {},
  methods: {
    navPage(e){
        console.log(e);
      this.$emit('page_html', e);
    },
    nextPage(){
      var c=this.page_html+1;
      this.$emit('page_html',c);
    },
    prePage(){
        var c=this.page_html-1;
      this.$emit('page_html',c);
    }


  },
  created() {},
  mounted() {}
};
</script>
<style lang="scss" scoped>
.rd_paging {
    display: flex;
    justify-content: flex-end;
    margin-top: 88px;
    padding-bottom: 120px;
}

.previous_page {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 80px;
    height: 36px;
    background: rgba(255, 255, 255, 1);
    border: 1px solid rgba(217, 217, 217, 1);
    margin-right: 12px;
    cursor: pointer;
}

.previous_page>img {
    width: 10px;
    height: 16px;
    margin-right: 5px;
}

.next_page {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 80px;
    height: 36px;
    background: rgba(255, 255, 255, 1);
    border: 1px solid rgba(217, 217, 217, 1);
    cursor: pointer;
}

.next_page>img {
    width: 10px;
    height: 16px;
    margin-left: 5px;
}

.rd_paging .pages {
    display: flex;
}

.rd_paging .pages block {
    display: flex;
}

.rd_paging .pages span {
    width: 36px;
    height: 36px;
    background: rgba(255, 255, 255, 1);
    border: 1px solid rgba(227, 227, 227, 1);
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 14px;
    color: #333333;
    margin-right: 12px;
    cursor: pointer;
}

.rd_paging .pages span.active {
    width: 36px;
    height: 36px;
    background: rgba(229, 0, 18, 1);
    color: #fff;
    border: 1px solid rgba(229, 0, 18, 1);
}

.rd_paging .pages span.e {
    font-size: 14px;
    color: #333333;
    width: 36px;
    height: 36px;
    display: flex;
    justify-content: center;
    align-items: center;
    margin-right: 12px;
}
</style>