<div style="background: green ">
<!-- top left -->
  <div>
    <img src="https://emojis.slackmojis.com/emojis/images/1563480763/5999/meow_party.gif" width="60" height="60"/> 
    <img src="https://emojis.slackmojis.com/emojis/images/1563480763/5999/meow_party.gif" width="60" height="60" align="right"/> 
</div>
<!-- first row -->

<p align="center">
<a href="http://shenbh.github.io"><img src="https://media.giphy.com/media/WUlplcMpOCEmTGBtBW/giphy.gif" width="30"></a>


# ☕Get In Touch
<p>
<a href="https://gitee.com/shen_bh"><img src="https://gitee.com/static/images/logo-black.svg?t=158106664" width="100"></a>
<p>
<a href="https://github.com/shenbh"><img src="https://img.shields.io/badge/-Github-000?style=flat&logo=Github&logoColor=white"></a>

[![Blog](https://img.shields.io/badge/-Website-FCA121?style=flat&logo=java&logoColor=white)](http://shenbh.github.io/)

<a href="mailto:shenbh@qq.com"><img src="http://file.service.qq.com/user-files/uploads/201701/8b713d5a5557aec926f7b379f61843ed.png" width="100"></a>




# AB's Blog

博客地址：http://shenbh.github.io


## About Blog

### 主题

博客使用的是 [next](https://github.com/iissnan/hexo-theme-next) 主题，版本是 `5.1.3`。



### 添加[Gitalk](https://github.com/gitalk/gitalk)评论

需要 `Github Application`，如果没有 [点击这里申请](https://github.com/settings/applications/new)，`Authorization callback URL` 填写你主页地址，比如我的就是 `https://shenbh.github.io`，其他都随意。

1. 首先创建 `Gitalk` 的 `swig` 文件，放在 `themes/next/layout/_third-party/comments` 文件夹下，命名为 `gitalk.swig` 。内容如下

```
{% if page.comments && theme.gitalk.enable %}
  <link rel="stylesheet" href="https://unpkg.com/gitalk/dist/gitalk.css">

  <script src="https://unpkg.com/gitalk/dist/gitalk.min.js"></script>
   <script type="text/javascript">
		var gitalk = new Gitalk({
		  clientID: '{{ theme.gitalk.ClientID }}',
		  clientSecret: '{{ theme.gitalk.ClientSecret }}',
		  repo: '{{ theme.gitalk.repo }}',
		  owner: '{{ theme.gitalk.githubID }}',
		  admin: ['{{ theme.gitalk.adminUser }}'],
		  id: location.pathname,
		  distractionFreeMode: '{{ theme.gitalk.distractionFreeMode }}'
		})
		gitalk.render('gitalk-container')           
       </script>
{% endif %}
```

1. 在主题文件 `themes/next/layout/_third-party/comments/index.swig` 中引入刚刚添加的文件。

```
{% include 'gitalk.swig' %}
```

1. 在 `themes/next/layout/_partials/comments.swig` 文件末找到倒数第二个 `endif` 语句，在前面插入如下代码:

```
{% elseif theme.gitalk.enable %}
  <div id="gitalk-container"></div>
```

1. 在 `themes/next/_config.xml` 文件中引入 `Gitalk`

```
gitalk:
  enable: true
  # 是否自动展开评论框
  autoExpand: true
  githubID: shenbh
  # issue仓库名
  repo: blog-comment
  # 应用编号
  ClientID: 2ee45ae794a910d593d1
  # 应用秘钥
  ClientSecret: b534b2e3af3e52e38b3b6ac032b3fb9d3f35cad5
  adminUser: shenbh
  distractionFreeMode: true
```

其中 `githubID` 是你的 `Github` 用户名，`repo` 是你用来存放评论 `issue` 的仓库，比如我的就是[blog-comment](https://github.com/Blankj/blog-comment)，那么我就写 `blog-comment` 即可，`ClientID` 和 `ClientSecret` 就是你之前申请 `Github Application` 可以获取到，`adminUser` 和 `githubID` 一样即可，`distractionFreeMode` 是评论时遮照效果的开关。



### 添加背景图

在 `themes/next/source/css/_custom/custom.styl` 中添加如下代码：

```
body{
    background:url(/images/bg.jpg);
    background-size:cover;
    background-repeat:no-repeat;
    background-attachment:fixed;
    background-position:center;
}
```



### 修改Logo字体

在 `themes/next/source/css/_custom/custom.styl` 中添加如下代码：

```
@font-face {
    font-family: Blankj;
    src: url('/fonts/Blankj.ttf');
}

.site-title {
    font-size: 40px !important;
	font-family: 'Blankj' !important;
}
```

其中字体文件在 `themes/next/source/fonts` 目录下，里面有个 `.gitkeep` 的隐藏文件，打开写入你要保留的字体文件，比如我的是就是写入 `Blankj.ttf`，具体字库自己从网上下载即可。



### 设置圆形头像

修改 `themes/next/source/css/_common/components/sidebar/sidebar-author.styl` 为下方代码。

```
.site-author-image {
  display: block;
  margin: 0 auto;
  padding: $site-author-image-padding;
  max-width: $site-author-image-width;
  height: $site-author-image-height;
  border: $site-author-image-border-width solid $site-author-image-border-color;
  /* 头像圆形 */
  border-radius: 80px;
  -webkit-border-radius: 80px;
  -moz-border-radius: 80px;
  box-shadow: inset 0 -1px 0 #333sf;
  /* 设置循环动画 [animation: (play)动画名称 (2s)动画播放时长单位秒或微秒 (ase-out)动画播放的速度曲线为以低速结束
    (1s)等待1秒然后开始动画 (1)动画播放次数(infinite为循环播放) ]*/
  -webkit-animation: play 2s ease-out 1s 1;
  -moz-animation: play 2s ease-out 1s 1;
  animation: play 2s ease-out 1s 1;
  /* 鼠标经过头像旋转360度 */
  -webkit-transition: -webkit-transform 1.5s ease-out;
  -moz-transition: -moz-transform 1.5s ease-out;
  transition: transform 1.5s ease-out;
}
img:hover {
  /* 鼠标经过停止头像旋转
  -webkit-animation-play-state:paused;
  animation-play-state:paused;*/
  /* 鼠标经过头像旋转360度 */
  -webkit-transform: rotateZ(360deg);
  -moz-transform: rotateZ(360deg);
  transform: rotateZ(360deg);
}
/* Z 轴旋转动画 */
@-webkit-keyframes play {
  0% {
    -webkit-transform: rotateZ(0deg);
  }
  100% {
    -webkit-transform: rotateZ(-360deg);
  }
}
@-moz-keyframes play {
  0% {
    -moz-transform: rotateZ(0deg);
  }
  100% {
    -moz-transform: rotateZ(-360deg);
  }
}
@keyframes play {
  0% {
    transform: rotateZ(0deg);
  }
  100% {
    transform: rotateZ(-360deg);
  }
}
.site-author-name {
  margin: $site-author-name-margin;
  text-align: $site-author-name-align;
  color: $site-author-name-color;
  font-weight: $site-author-name-weight;
}
.site-description {
  margin-top: $site-description-margin-top;
  text-align: $site-description-align;
  font-size: $site-description-font-size;
  color: $site-description-color;
}
```