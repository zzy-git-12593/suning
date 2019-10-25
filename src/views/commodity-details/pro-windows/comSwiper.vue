<!--上方导航弹窗-->
<template>
    <div class="comswiper-top-tc">
        <p @click="comSwiperDownClick">
            <span class="el-icon-close"></span>
        </p>
        <div class="comswiper-top-tc-content">
            <div class="comswiper-top-tc-content-top">
                快速导航
            </div>
            <ul>
                <li @click="backHome">
                    <div>
                        <span class="el-icon-school"></span>
                    </div>
                    <div>首页</div>
                </li>
                <li @click="backShopCar">
                    <div>
                        <span class="el-icon-shopping-cart-1"></span>
                    </div>
                    <div>购物车</div>
                </li>
                <li @click="goSearch">
                    <div>
                        <span class="el-icon-search"></span>
                    </div>
                    <div>搜索</div>
                </li>
                <li @click="backType">
                    <div>
                        <span class="el-icon-menu"></span>
                    </div>
                    <div>全部分类</div>
                </li>
                <li @click="backMy">
                    <div>
                        <span class="el-icon-user"></span>
                    </div>
                    <div>我的易购</div>
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
    methods: {
        comSwiperDownClick() {
            this.$emit('com-swiper-down-click')
        },
        backHome() {
            if (this.$route.path != "/homepage/home") {
                this.$router.push("/homepage/home");
            }
            // 监听homeIconShow 绑定导航栏图标和返回顶部按钮的显示
            if (this.homeIconShow) {
                window.scrollTo(0, this.likeOffsetTOP - this.goodShopOffsetHeight);
                this.homeIconShow = false;
            } else {
                window.scrollTo(0, 0);
                this.homeIconShow = true;
            }
            // 使用路由地址判断使控制导航点击calss的添加。
            this.index = this.$route.path;
        },
        backType() {
            if (this.$route.path != "/homepage/type") {
                this.$router.push("/homepage/type");
            } else {
                this.$router.push("/search");
            }
            if (this.homeIconShow) {
                this.homeIconShow = false;
            }
        },
        backOhter() {
            // if (this.$route.path != "/homepage/other") {
            //   this.$router.push("/homepage/other");
            // }
        },
        goSearch() {
            if (this.$route.path == "/search/searchover") {
                this.$router.push("/search");
            }
        },
        backShopCar() {
            if (this.$route.path != "/homepage/shoppingcar") {
                this.$router.push("/homepage/shoppingcar");
            }
            if (this.homeIconShow) {
                this.homeIconShow = false;
            }
        },
        backMy() {
            if (this.$route.path != "/homepage/myyglogin") {
                this.$router.push("/homepage/myyglogin");
            }
            if (this.homeIconShow) {
                this.homeIconShow = false;
            }
        }
    }
}
</script>

<style scoped>
*{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
.comswiper-top-tc p:first-child{
    padding: 10px;
    display: flex;
    justify-content: flex-end;
}
.comswiper-top-tc p:first-child .el-icon-close{
    font-size: 25px;
    color: #222;
    border-radius: 50%;
    background-color: #fff;
    padding: 5px;
}
.comswiper-top-tc-content{
    width: 100%;
    background-color: #fff;
    padding: 10px;
    border-radius: 8px;
}
.comswiper-top-tc-content-top{
    width: 100%;
    color: #222;
    font-size: 15px;
    padding: 10px 20px 0;
}
.comswiper-top-tc ul{
    list-style: none;
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    padding: 10px 20px 0;
}
.comswiper-top-tc ul li{
    background-color: powderblue;
    width: 22%;
    font-size: 12px;
    color: #333;
    text-align: center;
    margin: 10px 0; 
    border-radius: 4px;
    padding: 8px;
}
.comswiper-top-tc ul li div:first-child{
    font-size: 30px;
}
</style>