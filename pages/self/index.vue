<template>
	<view>
		<uni-fab :pattern="pattern" :content="content" :horizontal="horizontal" :vertical="vertical" :direction="direction"
				 @trigger="trigger" ref="fab"></uni-fab>
	</view>
</template>

<script>
    import uniIcon from '@/components/uni-icon/uni-icon.vue';
    import uniFab from '@/components/uni-fab.vue';
    export default {
        data() {
            return {
                horizontal: 'left',
                vertical: 'bottom',
                direction: 'horizontal',
                pattern: {
                    color: '#7A7E83',
                    backgroundColor: '#fff',
                    selectedColor: '#007AFF',
                    buttonColor: '#007AFF'
                },
                content: [{
                    iconPath: '/static/png/tabBar/team1.png',
                    selectedIconPath: '/static/png/tabBar/team2.png',
                    text: '组件',
                    active: false
                },
                    {
                        iconPath: '/static/api.png',
                        selectedIconPath: '/static/apiHL.png',
                        text: 'API',
                        active: false
                    },
                    {
                        iconPath: '/static/template.png',
                        selectedIconPath: '/static/templateHL.png',
                        text: '模版',
                        active: false
                    }
                ]
            };
        },
        methods: {
            trigger(e) {
                console.log(e);
                this.content[e.index].active = !e.item.active;
                uni.showModal({
                    title: '提示',
                    content: `您${this.content[e.index].active ? '选中了' : '取消了'}${e.item.text}`,
                    success: function(res) {
                        if (res.confirm) {
                            console.log('用户点击确定');
                        } else if (res.cancel) {
                            console.log('用户点击取消');
                        }
                    }
                });
            },
        },
        components: {
            uniFab,
            uniIcon
        }
    };
</script>

<style>
	.btn {
		margin: 30upx 0;
	}
</style>
