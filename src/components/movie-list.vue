<template>
  <div class="md-movie-list">
    <view class="list">
      <template v-if="type !== 'us_box'">
        <navigator :url="'../item/item?id=' + item.id" v-for="(item, index) in movies" :key="item.id">
          <movie-item :movie="item"></movie-item>
        </navigator>
      </template>
      <template v-else>
        <navigator :url="'../item/item?id=' + item.subject.id" v-for="(item, index) in movies" :key="item.rank">
          <movie-item :movie="item.subject"></movie-item>
        </navigator>
      </template>
      <view class="tips">
        <view v-if="hasMore">
          <image src="/static/images/loading.gif" mode="aspectFill"/>
          <text>正在加载...</text>
        </view>
        <view v-else>
          <text>--------------- 我也是有底线的 --------------</text>
        </view>
      </view>
    </view>
  </div>
</template>

<script>
import MovieItem from '@/components/movie-item'

export default {
  components: {
    'movie-item': MovieItem
  },

  props: {
    movies: {
      type: Array,
      default () {
        return []
      }
    },
    hasMore: {
      type: Boolean,
      default: true
    },

    type: String
  }
}
</script>

<style>
.list {
  height: 100%;
}

.list .item {
  display: flex;
  padding: 20rpx 40rpx;
  border-bottom: 1rpx solid #eee;
  cursor: pointer;
}

.list .item .poster {
  width: 128rpx;
  height: 168rpx;
  margin-right: 20rpx;
}

.list .item .meta {
  flex: 1;
}

.list .item .meta .title,
.list .item .meta .sub-title {
  display: block;
  margin-bottom: 15rpx;
}

.list .item .meta .title {
  font-size: 32rpx;
}

.list .item .meta .sub-title {
  font-size: 22rpx;
  color: #c0c0c0;
}

.list .item .meta .artists {
  font-size: 24rpx;
  color: #999;
}

.list .item .rating text {
  display: inline-block;
  width: 40rpx;
  font-size: 28rpx;
  font-weight: bold;
  text-align: center;
  background-color: rgba(247, 76, 49, 0.8);
  color: #fff;
  padding: 10rpx;
  border-radius: 20rpx;
}

.list .tips {
  font-size: 28rpx;
  text-align: center;
  padding: 50rpx;
  color: #ccc;
}

.list .tips image,
.list .tips text {
  vertical-align: middle;
}

.list .tips image {
  width: 40rpx;
  height: 40rpx;
  margin-right: 20rpx;
}

.header {
  display: flex;
  justify-content: center;
  border-bottom: 1rpx solid #ccc;
}


.header text {
  padding: 20rpx 40rpx;
  color: #999;
  font-size: 38rpx;
  text-align: center;
}

</style>
