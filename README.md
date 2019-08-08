<h1>HTML实现九宫格延伸特效</h1>

利用HTML实现九宫格延伸特效，当鼠标悬浮到某一张图片上时，可以按照既定设计延伸出更多图片。

![](demo.gif)

**一、添加背景**

设置背景图片及大小，注意调整浏览器默认配置，比如padding、margin等，不然换个浏览器可能就样式完全变了。

```html
    *{/*通配符：匹配页面所有元素*/
            margin: 0;
            padding: 0;
    }
    body{
        background:url("./images/bg.jpg") no-repeat; /*复合写法 颜色 背景图片  位置……*/
        background-size: 100% 100%;
    }
```

**二、九宫格布局**

利用div为框架，中间设置ul无序列表，布局为浮动排列，设置好九宫格展示。

```html
    #box{
        width: 906px;
        height: 486px;
        background-color: #6699cc;
        border: 5px solid #ffffff;/*边框： 大小 实线 颜色*/
        margin: 100px auto;/*上下100 左右自适应*/
    }
    #box ul li{
        position: relative;/*相对定位 参考物*/
        float: left; /*浮动 让元素从左到右横排显示*/
        list-style: none;/*去掉小圆点*/
        width: 300px;
        height: 160px;
        background: #6633ff;
        border: 1px solid #fff;
    }
```

**三、添加图片、文字**

利用img、p标签添加图片文字，进一步设置样式居中及背景样式

```html
    #box ul li img{
        position: absolute;/*绝对定位，相当于运动的人*/
        left: 0;
        top: 0;
        opacity: 0;
        transition: .5s;
    }
    #box ul li p{
        position: absolute;/*绝对定位，相当于运动的人*/
        left: 0;
        top: 0;
        width: 100%;
        height: 100%;
        font-size: 20px;
        color: #fff;
        text-align: center;
        line-height: 160px;
        opacity: 0; /*透明度*/
        background: rgba(0, 0, 0, .7);
        transition: .5s;
    }
```

**四、设置延伸效果**

通过层级z-index将默认图片部署到页面最上层，利用opacity设置透明度，需要延伸的图片设置为0，延伸特效后设置为1，默认显示图片设置相反，延伸特效主要是利用hover进行设置，即鼠标点击后显示需要延伸的图片，设置好透明度和延伸方向即可，延伸速度可以通过transition设置时间。

```html
    #box ul li img.first{
        opacity: 1;
    }
    #box ul li:hover img.right{
        left: 302px;
        z-index: 999;
        opacity: 1;
    }
    #box ul li:hover img.left{
        left: -302px;
        z-index: 999;
        opacity: 1;
    }
    #box ul li:hover img.bottom{
        top: 162px;
        z-index: 999;
        opacity: 1;
    }
    #box ul li:hover img.top{
        top: -162px;
        z-index: 999;
        opacity: 1;
    }
    #box ul li:hover p{
        opacity: 1;
    }
```
