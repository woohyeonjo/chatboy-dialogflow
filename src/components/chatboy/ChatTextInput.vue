<template>
    <div class="nnm__input-bar">
        <div class="nnm__input-bar-inner">
            <input class="nnm__input-text" v-on:keyup.enter="sendChat" v-model="inputText"
                   placeholder="Message" autocomplete="off" />
            <h6 @click="sendChat">Send</h6>
        </div>
    </div>
</template>

<script>
    export default {
        name: "ChatTextInput",
        data () {
            return {
                inputText: '',
            }
        },
        methods: {
            clearInput() {
                this.inputText = '';
            },
            sendChat() {
                if(this.inputText === '') return;
                this.$store.commit('sendMessage', this.inputText);
                this.clearInput();
                this.$store.dispatch('question');
            }
        }
    }
</script>

<style lang="scss" scoped>
.nnm__input-bar {
    display: flex;
    justify-content: center;
    height: 80px;
    border-bottom-left-radius: 10px;
    border-bottom-right-radius: 10px;
    background-color: #F1F1F1;
}
.nnm__input-bar-inner {
    margin: 15px;
    height: 49px;
    border-radius: 7px;
    background-color: white;
    h6 {
        float: right;
        font-size: 20px;
        margin-top: 14px;
        margin-left: 10px;
        margin-right: 27px;
        color: #381e1f;
        font-weight: 400;
        -webkit-transition: all 0.3s ease-in-out;
        -moz-transition: all 0.3s ease-in-out;
        -o-transition: all 0.3s ease-in-out;
        -ms-transition: all 0.3s ease-in-out;
        &:hover {
            opacity: 0.3;
            cursor: pointer;
        }
    }

}
.nnm__input-text {
    font-size: 17px;
    text-align: center;
    margin-left: 10px;
    margin-top: 14px;
    width: 300px;
    font-family: inherit;
    font-weight: 400;
    border: none;
    border-right: solid 2px #F1F1F1;
    &:focus {
        outline: none;
    }
}
</style>