<!-- 关于作者 -->
<template>
  <view class="about">

    <canvas canvas-id="bubble" :style="'width:' + width + 'px;height:' + height + 'px'" class="like-fx"></canvas>
    <like-fx ref="likeFx" :width="width" :height="height"></like-fx>

	<view class="titleZ text-center align-center">
		<text class="text-bold">使用说明</text>
		<view class="contentZ"style="margin-top: 40rpx;">
      <text class="text-xl text-center align-center">❤</text>
      <text class="text-xl">你好呀，欢迎来到</text>
      <text class="text-xl text-bold">「小智的世界」！</text>
			<text class="text-xl">O(∩_∩)O我的技能有课程推荐，询问专业，询问课程名，询问查询项目，闲聊，一起来一场愉快的对话吧！</text>
      <text class="text-xl">❤</text>
    </view>
	</view>
    <button @click="toPage('../index/tabbar')">
      <image src='../../static/img/log.png' class='share-img png round shadow-lg bg-white' mode='aspectFit'>
      </image>
    </button>
  </view>
<!--  <canvas canvas-id="bubble" :style="'width:' + width + 'px;height:' + height + 'px'" class="like-fx"></canvas>-->
<!--  <like-fx ref="likeFx" :width="width" :height="height"></like-fx>-->
<!--  <view class="titleZ text-center align-center">-->
<!--    <text class="text-bold">你好呀O(∩_∩)O</text>-->
<!--  </view>-->
<!--  <view class="titleZ text-center align-center margin-top-xl">-->
<!--    <view class="contentZ" style="margin-top: 40rpx;">-->
<!--      <text class="text-xl text-center align-center">❤</text>-->
<!--      <text class="text-xl">欢迎来到</text>-->
<!--      <text class="text-xl text-bold">「小智的世界」</text>-->
<!--      <text class="text-xl">我的技能有课程推荐，询问专业，询问课程名，询问查询项目，闲聊，一起来一场愉快的对话吧！</text>-->
<!--      <text class="text-xl">❤</text>-->
<!--    </view>-->
<!--  </view>-->
</template>

<script>
  import LikeFx from '@/components/likeFx/likeFx.vue'
  export default {
    components: {
      LikeFx
    },
    data() {
      return {
        animation_timer: null, // 动画定时器
        width: 375,
        height: 1920
      }
    },
    onLoad() {
      this._startLikeAnimation();
    },
    onShareAppMessage() {
      return {
        title: '快来和我们玩转软件开发吧～',
        path: '/pages/about/about?from=share'
      }
    },
    methods: {
      toPage(page){
        uni.navigateTo({
          url: page
        });
      },
      _startLikeAnimation() {
        this.animation_timer = setInterval(() => {
          this.$refs.likeFx.likeClick()
        }, 300)
      }
    }
  }
</script>

<style scoped>
	.titleZ{
		width: 750rpx;
		font-size: 52rpx;
		margin-top: 60rpx;
	}
	.contentZ{
		width: 650rpx;
		margin: 10rpx auto 0;
		text-align: left;
	}
  .about-bg {
    background-size: cover;
    width: 100vw;
    height: 100vh;
    justify-content: center;
    flex-direction: column;
    color: #fff;
  }

  .edit-fixed {
    position: fixed;
    width: 100%;
    bottom: 0;
    z-index: 1024;
    box-shadow: 0 1rpx 6rpx rgba(0, 0, 0, 0.1);
  }

  .detail-imgs image {
    width: 100%;
    float: left;
    /* height:400rpx; 不定高了*/
    border: 0;
    padding: 0;
    margin: 0
  }

  .share-img {
    position: fixed;
    padding: 10rpx;
    width: 100rpx;
    height: 100rpx;
    /* top: 680rpx; */
    bottom: 200rpx;
    right: 20rpx;
    z-index: 1024;
    opacity: 0.8;
    box-shadow: 0rpx 8rpx 30rpx 0rpx rgba(0, 0, 0, 0.3);
    border: none;
  }

  .about {
    margin: 0;
    width: 100%;
    height: 100vh;
	padding-top: 20%;
    color: #fff;
    background: linear-gradient(-120deg, #F15BB5, #9A5CE5, #01BEFF, #00F5D4);
    /* background: linear-gradient(-120deg, #0976ea, #c471f5, #f956b6, #ea7e0a); */
    background-size: 500% 500%;
    animation: gradientBG 15s ease infinite;
  }

  @keyframes gradientBG {
    0% {
      background-position: 0% 50%;
    }

    50% {
      background-position: 100% 50%;
    }

    100% {
      background-position: 0% 50%;
    }
  }

  .container {
    width: 100%;
    position: absolute;
    text-align: center;
  }

  .like-fx {
    position: fixed;
    right: 0;
    z-index: 1024;
    pointer-events: none;
    /* background-color: red; */
  }
</style>
