<template>
    <div>
        <div class="sidebar-extend" @mousemove="extend()" v-show="extendIsShow">
            <img src="../assets/img/siderightbar/sidebar-extend.png" alt="">
        </div>
        <!-- 一级菜单 -->
        <div class="sidebar" v-show="sidebarIsShow">
            <div class="sidebar-shrink" @mousemove="shrink()">
                <img src="../assets/img/siderightbar/sidebar-shrink.png" alt="">
            </div>
            <div class="sidebar-box">
                <div class="sidebar-box-iconbox">
                    <ul>
                        <template v-for="(item, index) in menus">
                            <li class="item" :key="index">
                                <div class="icon">
                                    <i class="icon iconfont" :class="item.icon" @click="iconClick($event,item)"></i>
                                </div>
                                <!-- 二级菜单 -->
                                <div class="secondary-menu-box" v-show="secondaryMenuShow">
                                    <ul>
                                        <template v-for="(item, index) in secondaryMenus">
                                            <li :key="index">
                                                <i class="icon iconfont" :class="item.icon"></i>
                                            </li>
                                        </template>
                                    </ul>
                                </div>
                            </li>
                        </template>
                    </ul>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'SideRightBar',
    data() {
        return {
            menus: [{
                    icon: "icon-tuceng"
                },
                {
                    icon: "icon-moxingku"
                },
                {
                    icon: "icon-chizi"
                },
                {
                    icon: "icon-diqiuxueyuan"
                },
                {
                    icon: "icon-huanyuan"
                },
                {
                    icon: "icon-suodingtouming_huaban1"
                },
                {
                    icon: "icon-guangshijiao"
                },
                {
                    icon: "icon-pouqie"
                },
                {
                    icon: "icon-caijian"
                },
            ],
            secondaryMenus: [{
                    icon: "icon-tuceng"
                },
                {
                    icon: "icon-moxingku"
                },
                {
                    icon: "icon-chizi"
                }
            ],
            extendIsShow: true,
            sidebarIsShow: false,
            secondaryMenuShow: false,
            currentIndex: "",
        };
    },
    methods: {
        extend() {
            this.extendIsShow = false;
            this.sidebarIsShow = true
        },
        shrink() {
            this.extendIsShow = true;
            this.sidebarIsShow = false
        },
        iconClick(e,item) {
            this.secondaryMenuShow = true
            var secondaryMenu = document.querySelector(".secondary-menu-box")
            const rect = e.target.getBoundingClientRect() //获取点击的dom的位置
            secondaryMenu.style.
            e.currentTarget.style.color = "red"
            console.log(e.currentTarget);
            console.log(rect)
        }
    }
}
</script>

<style>
.sidebar {
    position: absolute;
    top: 50%;
    right: 0;
    transform: translate(0, -50%);
}

.sidebar-extend {
    position: absolute;
    top: 49%;
    right: 0;
    transform: translate(0, -50%);
    cursor: pointer;
}

.sidebar-shrink {
    position: absolute;
    right: 37px;
    top: 170px;
    cursor: pointer;
}

.sidebar-shrink:hover {
    opacity: 0.9;
}

.sidebar-extend:hover {
    opacity: 0.9;
}

.sidebar-box {
    width: 39px;
    height: 401px;
    background-image: url("../assets/img/siderightbar/sidebar-box.png");
}

.sidebar-box-iconbox {
    padding-left: 12px;
    padding-top: 30px;
}

.sidebar-box-iconbox li {
    margin-top: 20px;
    cursor: pointer;
}

.sidebar-box-iconbox li:hover {
    opacity: 0.8;
}

.sidebar-box-iconbox li :hover {
    color: #26ceff;
}

.secondary-menu-box {
    position: absolute;
    top: 363px;
    right: 0;
    width: 152px;
    height: 34px;
    cursor: pointer;
    background-image: url("../assets/img/siderightbar/Secondarymenu-box.png");
}

.secondary-menu-box ul {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    padding-top: 9px;
    padding-left: 5px;
}
</style>
