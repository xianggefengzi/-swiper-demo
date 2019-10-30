<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div class="Case">
      <div v-for="(item,index) in CaseList" :key="item.index" @click="SwitchoverScene(index)">
        <div :class="item.isClick ? 'switchover2' : 'switchover1' ">{{item.label}}</div>
      </div>
    </div>

    <swiper :options="swiperOption">
      <swiper-slide v-for="item in imgList" :key="item.id">
        <img :src="item.content">
      </swiper-slide>   
      <!-- <div class="swiper-pagination" slot="pagination"></div> -->
      <div class="swiper-button-prev" slot="button-prev"></div>
      <div class="swiper-button-next" slot="button-next"></div>
    </swiper>
  </div>
</template>

<script>
import 'swiper/dist/css/swiper.css'
import { swiper, swiperSlide } from 'vue-awesome-swiper'
export default {
  name: 'HelloWorld',
  components: {
    swiper,
    swiperSlide
  },
  data () {
    return {
      msg: '使用 swiper 写轮播图',
      swiperOption: {
        observer:true,//修改swiper自己或子元素时，自动初始化swiper 
        observeParents:true,//修改swiper的父元素时，自动初始化swiper 
        slidesPerView: 3, // 显示三张图片
        spaceBetween: 1, //图片与图片直接的距离
        // loop : true, //无缝滚动
        // autoplay:true, // 自动滚动
        autoplay: {
          delay: 3000,
          stopOnLastSlide: false, // 自动循环播放 true 则不会
          disableOnInteraction: false, // 鼠标拖拽后还会自动播放 true 则是不会
        },
        grabCursor : true, // 鼠标放在图片上变成小手
        // pagination: {
        //   el: '.swiper-pagination',
        //   clickable: true
        // },
        navigation: {
          nextEl: '.swiper-button-next',
          prevEl: '.swiper-button-prev'
        }
      },
      CaseList:[
        {
          label:'电商',
          isClick:true,
          tupian:[
            {id:1,content:require("@/assets/12_ds_01.png")},
            {id:2,content:require("@/assets/12_ds_02.png")},
            {id:3,content:require("@/assets/12_ds_01.png")},
            {id:4,content:require("@/assets/12_ds_02.png")}
          ]
        },
        {
          label:'网点',
          isClick:false,
          tupian:[
            {id:1, content:require("@/assets/12_wd_01.png")},
            {id:2, content:require("@/assets/12_wd_02.png")},
            {id:3, content:require("@/assets/12_wd_03.png")},
            {id:4, content:require("@/assets/12_wd_04.png")},
            {id:5, content:require("@/assets/12_wd_05.png")},
            {id:6, content:require("@/assets/12_wd_06.png")}
          ]
        },
        {
          label:'商城',
          isClick:false,
          tupian:[
            {id:1, content:require("@/assets/12_sc_01.png")},
            {id:2, content:require("@/assets/12_sc_02.png")},
            {id:3, content:require("@/assets/12_sc_03.png")},
            {id:4, content:require("@/assets/12_sc_04.png")}
          ]
        },
        {
          label:'商圈/社区',
          isClick:false,
          tupian:[
            {id:1,content:require("@/assets/12_sq_01.png")},
            {id:2,content:require("@/assets/12_sq_02.png")},
            {id:3,content:require("@/assets/12_sq_03.png")},
            {id:4,content:require("@/assets/12_sq_01.png")},
            {id:5,content:require("@/assets/12_sq_02.png")},
            {id:6,content:require("@/assets/12_sq_03.png")},
          ]
        },
        {
          label:'专业市场',
          isClick:false,
          tupian:[
            {id:1,content:require("@/assets/12_zysc_01.png")},
            {id:2,content:require("@/assets/12_zysc_02.png")},
            {id:3,content:require("@/assets/12_zysc_03.png")},
            {id:4,content:require("@/assets/12_zysc_01.png")},
            {id:5,content:require("@/assets/12_zysc_02.png")},
            {id:6,content:require("@/assets/12_zysc_03.png")},
          ]
        },
        {
          label:'政企',
          isClick:false,
          tupian:[
            {id:1,content:require("@/assets/12_zq_01.png")},
            {id:2,content:require("@/assets/12_zq_02.png")},
            {id:3,content:require("@/assets/12_zq_03.png")},
            {id:4,content:require("@/assets/12_zq_01.png")},
            {id:5,content:require("@/assets/12_zq_02.png")},
            {id:6,content:require("@/assets/12_zq_03.png")},
          ]
        }
      ],
      imgList:[]
    }
  },
  created() {
    this.SwitchoverScene(0)
  },
  methods:{
    SwitchoverScene(index) {
      this.CaseList.forEach(val => {
        val.isClick = false;
      });
      this.CaseList[index].isClick = true;
      // 获取到轮播图需要的图片
      this.imgList = []
      this.imgList = this.CaseList[index].tupian
      // console.log(this.imgList,'imgList');
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
