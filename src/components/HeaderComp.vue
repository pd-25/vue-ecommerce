<template>
    <header id="myDIV" class="main-header" :class="{fixTop : 'sticky-header'}" @scroll="handleScroll">
        <div class="header-content">
            <ul class="left">
                <li><router-link class="routerLink" to="/">Home</router-link></li>
                <li><router-link class="routerLink" to="/about">About</router-link></li>
                <li>Categories</li>
            </ul>
            <div class="center">Ecom Store</div>
            <div class="right">
                <!-- <TbSearch /> -->

                <font-awesome-i icon="fa-solid fa-search" />
                <!-- <AiOutlineHeart /> -->
                <font-awesome-i icon="fa-solid fa-heart" />
                <span class="cart-icon">
                    <!-- <CgShoppingCart /> -->
                    <font-awesome-i icon="fa-solid fa-cart-shopping" />
                    <span>4</span>
                </span>
            </div>
        </div>
    </header>
</template>

<script>
export default {
    name: 'HeaderComp',
    data() {
        return {
            scrollTop: 0,
           
        };
    },
    created() {

        window.addEventListener('scroll', this.handleScroll);

    },

    unmounted() {

        window.removeEventListener('scroll', this.handleScroll);

    },
    methods: {
        handleScroll(event) {
            this.scrollTop = window.scrollY;
           if(this.scrollTop > 200) {
            // document.getElementById("myDIV").element.classList.add(" sticky-header");
            fixTop = 1;
           }else {
            // document.getElementById("myDIV").element.classList.remove("sticky-header");
            fixTop = 0;

           }
        },

    },
};
</script>

<style lang="scss">
@import "../../css-config/mixins.scss";

.main-header {
    width: 100%;
    padding: 0 20px;
    background-color: #212121;
    color: white;
    border-bottom: 1px solid rgba(0, 0, 0, 0.1);
    z-index: 99;

    @include md {
        padding: 0px 0px;
        margin-top: -8px;
    }

    .header-content {
        display: flex;
        justify-content: space-between;
        align-items: center;
        height: 74px;
        max-width: 1200px;
        margin: 0px 8px;
        margin-top: -8px;

        @include md {
            height: 80px;
        }

        .left {
            list-style-type: none;
            display: none;
            gap: 25px;

            @include md {
                display: flex;
            }

            li {
                font-size: 14px;
                font-weight: 600;
                text-transform: uppercase;
                cursor: pointer;
            }

        }

        .center {
            font-size: 22px;
            font-weight: 700;
            cursor: pointer;

            @include md {
                font-size: 34px;
                position: absolute;
                left: 50%;
                transform: translate(-50%);
            }
        }

        .right {
            display: flex;
            align-items: center;
            gap: 20px;

            @include md {
                gap: 25px;
            }

            svg {
                font-size: 20px;
                cursor: pointer;

                @include md {
                    gap: 25px;
                }
            }

            .cart-icon {
                position: relative;

                span {
                    min-width: 20px;
                    text-align: center;
                    background-color: #8e2de2;
                    padding: 2.5px;
                    position: absolute;
                    top: -5px;
                    right: -12px;
                    font-size: 12px;
                    line-height: 1;
                    border-radius: 10px;
                }
            }
        }
    }

    &.sticky-header {
        position: sticky;
        top: 0;
        transform: translateY(-80px);
        animation: stickyHeader 0.3s ease forwards;
    }
}

.routerLink {
    text-decoration: none;
    color: white;
}

@keyframes stickyHeader {
    0% {
        transform: translateY(-80px);
    }

    100% {
        transform: translateY(0);
    }
}
</style>