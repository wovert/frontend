# Frontend

## 移动端主流框架

- touchweb(手机网站)
- web-app(phoneGap appcan 打包成 安卓apk/苹果ios格式)
- hybrid-app(主流)
  - 特点: 性能不错/开发周期端
- native-app
  - 特点：性能高

- 性能排序：native-app < hybrid-app < web-app

## 移动端主流的 CSS 框架

- bootstrap 响应式布局
- Animate.css css3动画
- [nec 框架](http://nec.netease.com/framework)
- [icon字体](http://iconfont.cn/)

- SASS / Less 框架

## 移动主流JS

- zeptojs 库
- [jGestures 插件](https://archive.codeplex.com/?p=jgestures)
- swiper
- iScroll.js

## 移动开发框架

- jqueryMobile(性能差)
- [app framework](https://github.com/intel/appframework)
- senchtouch
- mobile angular ui
- phonegap
- appcan](http://www.appcan.cn/)
- [妹子UI](http://amazeui.org)
- [百度GMU](http://gmu.baidu.com)

## meta 属性

### viewport

``` H5
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta http-equiv="X-UA-Compatible" content="ie=edge">

width=device-width: 宽度是设备屏幕的宽度（像素）
height=device-height: 高度是设备屏幕的高度（像素）
initial-scale: 初始的缩放比例
minimum-scale: 允许用户缩放到的最小比例
maximum-scale: 允许用户缩放到最大比例
user-scalable: 用户是否可以手动缩放
```

### Format-detection

> 格式检测

meta name="format-detection" content="telephone=no"

meta name="format-detection" content="email=no"

meta name="format-detection" content="address=no"

meta name="format-detection" content="telephoneno,email=no,addres=no"

如果禁用，调用拨号功能可以这么写：`<a href="tel:4008106999,1034">400-810-6999 转 1034</a>`

`<a href="tel:15677776767">点击拨打15677776767</a>` 

### http-equiv

无缓存设置集中方法

1. `<meta http-equiv="Expires" content="-1">`

2. `<meta http-equiv="Cache-Control" content="no-cache">`

3. `<meta http-equiv="Pragma" content="no-cache">`

关于更多的meta，请看我之前的一篇文章：http://www.haorooms.com/post/html_meta_ds

## IOS 私有 meta 属性

### 第一个 meta

`<meta name="apple-mobile-web-app-capable" content="yes">` 网站开启对 web app 程序的支持。content为yes，Web 应用程序会以全屏幕模式运行，反之，则不会。contenet的默认值是 no,标识正常显示。可以通过只读属性 window.navigator.standalone 来确定网是否以全屏模式显示。

另外还有全屏显示的属性就是 `<meta name="apple-touch-fullscreen" content="yes" />` 为了更好的兼容，两个meta可以都写上！

### 第二个 meta

`<meta name="apple-mobile-web-app-status-bar-style" content="black" />`

在web app应用下状态条（屏幕顶部条）的颜色；
默认值为default（白色），可以定为black（黑色）和black-translucent（灰色半透明）。
注意：
若值为“black-translucent”将会占据页面px位置，浮在页面上方（会覆盖页面20px高度–iphone4和itouch4的Retina屏幕为40px）。

### IOS其他私有设置

添加主屏设置：

添加主屏幕之后，桌面图片和启动画面如何设置呢？

桌面图标设置：

``` H5
<link rel="apple-touch-icon" href="touch-icon-iphone.png" /> 带光感
<link rel="apple-touch-icon-precomposed" href="touch-icon-iphone.png" /> 设计原图
```

启动画面的设置

``` H5
<link rel="apple-touch-startup-image" href="milanoo_startup.png" /> 

可以指定不同尺寸

```

### 其他浏览器私有meta属性【除非特需，一般不推荐使用】

QQ浏览器私有

全屏模式
`<meta name="x5-fullscreen" content="true">`

强制竖屏
`<meta name="x5-orientation" content="portrait">`

强制横屏
`<meta name="x5-orientation" content="landscape">`

应用模式
`<meta name="x5-page-mode" content="app">`

### UC浏览器私有

全屏模式
`<meta name="full-screen" content="yes">`

强制竖屏
`<meta name="screen-orientation" content="portrait">`

强制横屏
`<meta name="screen-orientation" content="landscape">`

应用模式
`<meta name="browsermode" content="application">`

### 其它

针对手持设备优化，主要是针对一些老的不识别viewport的浏览器，比如黑莓

`<meta name="HandheldFriendly" content="true">`

微软的老式浏览器
`<meta name="MobileOptimized" content="320">`

windows phone 点击无高光
`<meta name="msapplication-tap-highlight" content="no">`

## 关于样式

### 上下拉动滚动条时卡顿、慢

``` CSS
body {
  -webkit-overflow-scrolling: touch;
  overflow-scrolling: touch;
}
```

### 禁止复制、选中文本

``` CSS
Element {
  -webkit-user-select: none;
  -moz-user-select: none;
  -khtml-user-select: none;
    user-select: none;
}
```

解决移动设备可选中页面文本(视产品需要而定)

### 长时间按住页面出现闪退

``` CSS
element {
  -webkit-touch-callout: none;
}
```

### iphone及ipad下输入框默认内阴影

``` CSS
Element{
  -webkit-appearance: none;
}
```

### ios和android下触摸元素时出现半透明灰色遮罩

``` CSS
Element {
  -webkit-tap-highlight-color:rgba(255,255,255,0)
}
```

设置alpha值为0就可以去除半透明灰色遮罩，备注：transparent的属性值在android下无效。

后面一篇文章有详细介绍，地址：http://www.haorooms.com/post/phone_web_ysk

### active兼容处理

`<body ontouchstart="">`

### 动画定义3D启用硬件加速

``` CSS
Element {
  -webkit-transform:translate3d(0, 0, 0)
  transform: translate3d(0, 0, 0);
}
```

注意：3D变形会消耗更多的内存与功耗

### Retina屏的1px边框

``` CSS
Element{
  border-width: thin;
}
```

### 旋转屏幕时，字体大小调整的问题

``` CSS
html, body, form, fieldset, p, div, h1, h2, h3, h4, h5, h6 {
  -webkit-text-size-adjust:100%;
}
```

### transition闪屏

``` CSS
设置内嵌的元素在 3D 空间如何呈现：保留3D
-webkit-transform-style: preserve-3d;

设置进行转换的元素的背面在面对用户时是否可见：隐藏
-webkit-backface-visibility:hidden;
```

### 圆角bug

``` CSS
某些Android手机圆角失效
background-clip: padding-box;
```

## 关于HTML5

### HTML5 中的一些有趣的新特性：

1. 用于绘画的 canvas 元素
2. 用于媒介回放的 video 和 audio 元素

demo:

``` H5
<video width="320" height="240" controls="controls">
  你浏览器不支持video
</video>
```

同理：

``` H5
<audio controls="controls">
  你浏览器不支持audio
</audio>
```

3. 对本地离线存储的更好的支持
4. 地理定位 navigator.geolocation.getCurrentPosition(callback,error,options)
5. 新的特殊内容元素，比如 article、footer、header、nav、section
6. 新的表单控件：

``` H5
email
url
number
range
Date pickers (date, month, week, time, datetime, datetime-local)
search
color
```

## 移动端基础架构

1. 项目需求
2. 技术选型
3. 项目的可扩展性、可维护性
4. 清晰地目录结构
5. 明确前后端分离
6. 产品出色的性能(js/css规范、js/css压缩合并、图片优化、延迟加载等等)
7. 模板的可复用性(yeomen脚手架工具来实现)
8. 服务器部署、发布流程
9. 安全

``` SHELL
# mkdir wxshop_sk
# cd wxshop_sk
# mkdir -pv static/{css,images,js,sass}
# cd static/js
# mkdir -pv {libs,plugs,views}
# cd ../sass
# mkdir -pv {layout,libs,plugs}
# cd ../../
#A tree
```

## SASS 安装

### ruby 安装

因为sass依赖于ruby环境，所以装sass之前先确认装了ruby。
先官网下载个[ruby](https://www.ruby-lang.org/en/documentation/installation/#homebrew) http://rubyinstaller.org/

``` shell
# sudo yum install ruby
# gem install sass
# gem install sas --pre 安装beta版本

从sass的Git repository来安装
# git clone git://github.com/nex3/sass.git
# cd sass
# rake install
# gem update sass 升级sass版本的命令
# sass -V
# sass -h

淘宝RubyGems 镜像安装 sass

由于国内网络原因，导致 rubygems.org 存放咋 Amazon S3 上面的资源文件间隙性连续失败。这时候我们可以通过 gem sources 命令来配置源，先移除默认的 https://rubygems.org 源，然后添加淘宝的源 https://ruby.taobao.org/, 然后查看下当前使用的源是那个，如果是淘宝的，则表示可以输入sass安装命令 `gem install sass`,关于常用 gem source 命令可参考：常用的 gem source

$ gem sosurces --remove https://rubygems.org/
$ gem sources -a https://ruby.taobao.org/
$ gem sources -l

https://ruby.taobao.org
$ gem isntall sass
```

### max 安装

``` shell
$ curl -L https://get.rvm.io | bash -s stable
$ source ~/.rvm/scripts/rvm
$ rvm -v
$ rvm install 2.0.0
$ gem -v
```

ERROR: Failed to build gem native extension.

``` SHELL
sudo gem uninstall sass
sudo gem uninstall compass
rvm install ruby-1.9.3-p448
sudo gem install sass --pre
sudo gem install compass --pre
```

## SASS 语法

``` SHELL
$ cd static/sass
$ vim test.sass

```