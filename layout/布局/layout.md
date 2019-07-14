## 百分比布局

### **视口标签**

```
<meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
```

![](F:\总结\images\视口标签.bmp)

### 背景缩放

backgrouna-size:  

cover 会覆盖整个盒子，溢出去的会切掉

contain 以宽度到为准，高度没到就没到，会全部显示在盒子中，会留有空白有时

**移动端初始化使用normalize.css**

**要设置最大宽度和最小宽度**

max-width:640px     min-widt:320px  

**二倍精灵图**

先在fw中把图片缩放一半，在代码里background-size也要写原来宽度的一半

## flex伸缩布局

给父元素一个display:flex;  子元素给flex需要几份就写几份 （flex:1;)，也可以写百分比   如  flex: 20%; 

给父盒子设为flex布局后，子元素的浮动，clear和vertical-align 属性将失效；

#### flex-direction

**控制主轴的方向**

**row** 默认值 水平分布 主轴x轴

**row-reverse** 水平反转

![](F:\总结\images\轴方向.bmp)

**colum**  垂直分布 主轴设为y轴，侧轴为x轴

#### justify-content

设置主轴上的子元素排列方式

**flex-start**   从左到右  默认值

**flex-end**   从尾部开始排列

**flex-center**  居中对齐

**flex-around**   平均分配  每个盒子的左右外边距相等

**flex-between**   两边的盒子贴边，然后再分配剩余空间  除去两边的盒子，中间的盒子左右外边距相等

#### flex-wrap 

控制子元素是否换行，默认不换行。如果装不开，会缩小子元素的大小，硬塞。

**nowrap**  不换行

**wrap**  换行

#### align-items （单行）

控制侧轴上的子元素排列方式

**flex-start**  默认值 从上到下

**flex-end** 从下到上

**center**  垂直居中

**strech**   拉伸  不给高度

如果想要单行的子元素在盒子中水平垂直居中 justify-content:center; 和 align-items: center;

#### align-content(多行)

控制侧轴上子元素排列方式，基本上要设置换行。

**flex-start**  侧轴头部开始排列

**flex-end**   从侧轴尾部开始排列

**center**   在侧轴中间显示

**space-between**    子项在侧轴两头分布，在分配剩余空间

**space-around**    子项在侧轴分配剩余空间

#### flex-flow 复合属性

**flex-direction**

**flex-wrap**

把主轴方向和是否换行（列）简写

**flex-flow：colum wrap；**

#### align-self

控制子项在侧轴上的排列方式，单独设置某个项目与其他不一样的对齐方式。

**align-self：flex-end；**

#### order

定义项目·的排序方式】数值越小排列越靠前默认0；可以设置为负数

一般父元素设置display：flex；子元素是行内元素，给了宽高度，就会转化为类似行内块，就不用再另行转换

#### 背景渐变

background: -webkit-linear-gradient (起始方向，颜色1，颜色2)；

background: -webkit-linear-gradient (left，top，颜色1，颜色2)；

起始方向可以是：方位名词也可以是度数，如果省略默认就是top。

## **rem布局**

#### rem单位

设置rem单位，可以控制整个页面所有元素有关PX类；（宽、高、padding、margin、top...）只要是你设置数值的地方都可以实现控制；

rem的基准是相对于html元素的字体大小来定的

em是相对于父元素的字体大小来定的  字体大小*em

rem的优势

可以通过修改html的文字大小来改变页面中元素的大小可以整体控制

#### 媒体查询

@media可以针对不同的屏幕设置不同的样式

**语法**

```
@media screen and (max-width: px) {
	html {
	font-size: px;
	}
}
```

min-width 定义页面中最小可见区域宽度

max-width 定义页面中最大可见区域宽度

![](F:\总结\images\3.png)

**划分挡位**  

档位1： max-width：539px；

档位2：min-width：540px；

档位3：min-width：970px；

**媒体查询类型****

all  用于所有设备

print  用于打印机和打印预览

screen  用于电脑屏幕，平板电脑，智能手机等

 **and | not | only 关键字**

关键字将  媒体类型    或   多个 媒体特性 连接到一起做为媒体查询的条件

and：可以将多个媒体特性连接到一起，相当于“且”的意思。！！最为常用

not：排除 某个 媒体类型，相当于“非”的意思，可以省略。@media  print  not {}

only：指定某个特定的 媒体类型，可以省略

**媒体查询+rem**

1.响应不同的屏幕尺寸，媒体查询

2.档位划分：从小到大

3.档位的划分是为了控制html字体的大小，下面所有子元素使用rem单位都可以变化

#### less基础

- **维护css的弊端**

css是一门非程序式语言，没有函数，变量等概念。

- **less介绍**

less是一门css扩展语言，也成为css预处理器。

- **less使用**

  **less变量**

  变量是指没有固定的值，可以改变的，因此在css中一些颜色和数值经常使用。

  @变量名：值；

  @color：pink；

  使用

  body {

  ​	color：@color；

  }

  **less嵌套**

  如果遇见 （交集|伪类|伪元素选择器） 

   内层选择器的前面没有 & 符号，则它被解析为父选择器的后代； 

  如果有 & 符号，它就被解析为父元素自身或父元素的伪类

  ```
  a:hover {
  	color:red;
  }
  ```

  **less嵌套写法**

  ```
  a {
  	&:hover {
  	color:red;
  	}
  }
  ```

  **less运算**

  任何数字，颜色或者变量都可以参与运算，就是less提供了加减乘除

  ```
  /*less里面写*/
  @width:10px+5;
  div {
  	border: @width solid red;
  }
  /*生成的css标签*/
  div {
  border: 15px solid red;
  }
  /*less还可以这样写*/
  width:(@width+5)*2
  ```

  **less运算注意**

  1. 乘号（*）和除号（/）的写法 
  2. 运算符中间左右有个空格隔开 1px + 5 
  3. 对于两个不同的单位的值之间的运算，运算结果的值取第一个值的单位   例如   15px+2em=17 px
  4. 如果两个值之间只有一个值有单位，则运算结果就取该单位

#### rem适配方案

​		1.为了不能等比自适应的元素，当设备尺寸发生变化的时候，等比列适配	当前设备

​		2.使用媒体查询根据不同设备按比列设置html的字体大小，页面元素使用	rem做尺寸单位，当html字体大小变化时元素尺寸也会发生变化，从而达到	等比所放的适配

##### **rem实际开发适配方案**

按照设计稿与设备宽度的比列，动态计算设置html根标签的font-size大小（媒体查询）；

css中，元素的大小和字体大小，都按照等比例换算为rem为单位的值

**rem适配方案两种**

技术方案1

**less+媒体查询+rem**

技术方案2

**flexibie.js+rem（简单）**

在index.html 中引入 flexible.js这个文件

<script src="js/flexible.js"> </script>



##### **rem值计算**

页面元素的rem值=页面元素值（px）/（屏幕的宽度/划分的份数）

750的屏幕划分为15份，50px就是html文字大小

屏幕的宽度/划分的份数就是html的font-size  字体大小

不同屏幕下得到的文字大小不一样

less先定义划分的份数 @no：15；

在index.less中引入common.less文件 @import"common";



## 响应式布局

### 屏幕宽度

xs 超小屏幕（手机之类）  小于768px    宽度设置为100%

sm 小屏幕 （平板之类）  大于等于768px  宽度设置为750px

md  中等屏幕 （桌面显示器） 大于等于992px  《992px  宽度设置为970px

lg  超大屏幕 （大显示器）   大于等于1200px  宽度设置为1170px

@media  screen and (max-width: 767px)  {

}	

```
/* 1. 超小屏幕下  小于 768  布局容器的宽度为 100% */
@media screen and (max-width: 767px) {
    .container {
        width: 100%;
    }
}


/* 2. 小屏幕下  大于等于768  布局容器改为 750px */
@media screen and (min-width: 768px) {
    .container {
        width: 750px;
    }
}


/* 3. 中等屏幕下 大于等于 992px   布局容器修改为 970px */
@media screen and (min-width: 992px) {
    .container {
        width: 970px;
    }
}

/* 4. 大屏幕下 大于等于1200 布局容器修改为 1170 */
@media screen and (min-width: 1200px) {
    .container {
        width: 1170px;
    }
}
```



### Bootstarp

引入外部标签

​    <!--[if lt IE 9]>

      <script src="https://oss.maxcdn.com/html5shiv/3.7.2/html5shiv.min.js"></script>
    
      <script src="https://oss.maxcdn.com/respond/1.4.2/respond.min.js"></script>

​    <![endif]-->

​    <!-- 引入bootstrap 样式文件 -->

​    <link rel="stylesheet" href="bootstrap/css/bootstrap.min.css">

​    <!-- 引入内部样式表 -->

.container 用于固定宽度并支持响应布局的容器

.container -fluid  用于100%宽度占据全部视口（viewport)的容器

#### 栅格系统

把版心 .container 划分分为12个栅格（列）

使用.col-md-* 这个类名，就可以划分12列每个占几列，md 在手机（xs）和在平板上（sm）是百分之百宽度的，和容器一样大,只有在中等屏幕（md)以上就会变为水平排列。  .container 必须包含.row 行，清除父亲的padding值，高度也会和父级一样高。所有的的col列必须在.row当中。

<div class

```
<div class="container">
	<div class="row">
		<div class="col-md-8"> 占八份 </div>
		<div class="col-md-4"> 占四份 </div>
	</div>
</div>
```

![](F:\总结\images\2019-05-06_104548.png)



###### 移动设备和桌面屏幕

​	如果不希望在小屏幕设备上所有的列堆叠在一起，就把.col-md 和.col-xs 混合在一起

```
<div class="container">
	<div class="row">
		<div class="col-xs-12 col-md-8"> 占八份 </div>
		<div class="col-xs-6 col-md-4"> 占四份 </div>
	</div>
</div>
```

![](F:\总结\images\2019-05-06_105900.png)

意思就是在xs-sm 中第一个div占据12列。第二个div只能另起一行占据六列。

而在中等屏幕以上第一个div占据八列，第二个div占据四列

列大于12，多余的列将会另起一行

在某些时候，有些列会出现比别的列高，解决方法，使用.clearfix和响应式工具类。

```
<div class="clearfix visible-xs-block> </div>"
```

##### 列偏移

.col-offest-n 可以将列向右偏移n列，其实就是增加了左侧的外边距margin

**列也可以嵌套**

##### 列排序

.col-md-pull-n 向右拉n列

.col-md-push-n 向左推n列

##### 不同屏幕尺寸隐藏或显示页面内容

**可见**

.visiadle-xs 指在超小屏幕下可见 xs可以更改 sm md lg

.visible-xs-inline-block 可见转化为行内块

.visible-xs-block 可见转化为块

.visible-xs-inline 可见转化为行内元素

**隐藏**

.hidden-xs 在超小屏幕下隐藏

## 布局总结



###  核心点

> 1. 【！！！】所有的移动端布局的核心思路，先看这个模块要不要设置高度，就是高度是否是固定的，没有高度的时候，就绝对是靠内部子元素撑起来的。
>
> 2. **注意移动端：body、定固定定位的元素设置伸缩保护。min-width   max-width**
>
> 3. 搜索区：
>    1. 盒子默认是100%宽度定位，搜索区中间部分没有设置宽度100%，使用margin进行定位和宽度的获取；
>    2. 修改搜索区为fixed定位，修改为定位后，里面的宽度响应的要设置100%宽度;
>    
> 4. 精灵图：1.firework缩小操作，测量。2.代码写入，3.图片大小设置（按照缩小的大小）;
>
> 5. 伪元素：某些左侧或右侧的线、或者简单的图标采用伪元素进行设置;
>
> 6. CSS3盒子：注意盒子模型的里面（新人礼包）;
>
> 7. 流式布局核心：靠百分比划分模块。
>
> 8. 结构伪类选择：n 作为参数，一定要放在前面
>
> 9. line-height:设置数字，此数字会与当前的字体尺寸相乘来设置行间距。
>
> 10. 流式布局，flex布局控制宽度
>
> 11. 在移动端，给盒子设置定位，不给left，top，什么，它还会在自身标准流的位置，不会进行移动，但还是会脱标，不占有位置。
>
> 12. **在rem布局中，宽度在媒体查询中大于640px的时候，要把它的html的font-size的值设为一个定值。而在最小宽度320px的时候，也要把它的html的font-size的值设为一个定值。否则在小于320px的时候，宽度虽然不会变化是定值，但其他的元素如高度会继续缩小，而宽度还是320px；**
>
>     ```
>     @media screen and (min-width: 640px) {
>     	html {
>     		font-size:64px!important;
>     	}
>     }
>     @media screen and (max-width: 320px) {
>     	html {
>     		font-size:32px!important;
>     	}
>     }
>     ```
>
>     



























































