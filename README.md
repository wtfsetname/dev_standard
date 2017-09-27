# 前端开发标准



## 必须遵守：

这是一份前端规范，志于提高开发效率

对于绑定js事件的DOM节点，必须有一个以"j-"为前缀的class

例子：

```html
<style>
  .u-btn {
      display: block;
      line-height: 30px;
      padding: 0 15px;
      background: #d95d4d;
      border-radius: 3px;
      color: white;
  }
</style>
<a class="u-btn j-remind">查看提示</a>
<script>
  $(function() {
      $('.j-remind').on('click', function() {
          //Your Code...
      })
  })
</script>
```

注意：j-remind不负责任何样式

加了"j-"前缀后的好处是明显的：开发人员能第一眼就看出该DOM节点是否绑定了事件，也能够迅速找到其对应的事件处理函数



## 建议（不强制）

###动态计算rem

移动端开发，可以加一段自适应屏幕的代码：

```javascript
!function(){
    function a(){
        if(parseInt(document.documentElement.clientWidth) > 720) {
            document.documentElement.style.fontSize=720/640*10/16*1000+"%";
        } else {
            document.documentElement.style.fontSize=document.documentElement.clientWidth/640*10/16*1000+"%";
        }
    }
    var b=null;
    window.addEventListener("resize",function(){
        clearTimeout(b);
        b=setTimeout(a,300);
    },!1);
    a();
}(window);
```

这段代码的最佳使用状态是：

设计稿给出640px的宽度，前端开发完全按照设计稿来，量出元素尺寸，并除以100

比如设计稿上的一个图案宽度130px，高度70px，转化一下就是1.3rem和0.7rem



### jQ对象命名加$

```javascript
//命名为$list，而非list
var $list = $('.m-list')
```



### 状态类

即"z-"为前缀的class，如下：

```html
<style>
.z-correct:after {
  content: '正确';
}
.z-error:after {
  content: '错误';
}
</style>
<div class="z-correct">
    我是人
</div>
<div class="z-error">
    我是猪
</div>
```

状态还有很多，如 认证状态 等。这样做的优点是：

```javascript
//添加了一个auth类
$('.m-control-panel').addClass('auth')
//添加了“已认证”状态
$('.m-control-panel').addClass('z-auth')
```



### 杂类

下面的都是抛砖引玉的作用：

```html
.g-xxx(grid) 布局，如：g-main
.m-xxx(module) 模块，如：m-slide
.u-xxx(unit) 元件，如：u-logo
.f-xxx(function) 功能，如：f-left
```

在已有semantic的情况下，再加入新的规范，两种风格混杂也未必是好事，所以说只是抛砖引玉的作用。
