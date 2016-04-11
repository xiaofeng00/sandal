# Sandal

sandal取其“檀香”之意，针对移动端站点为前端人员提供了一些基础的重置，常用的`mixin`，如flex布局，等分，水平垂直居中，常用图标等，基于它你可以扩展出更多你需要的组件。

## 更新说明
### 3.0版本
* 升级了语法，引入map函数，selector函数等
* 优化了mixin文件，优化了btn的mixin, 添加了retina 1px等
* icons采用绘制及svg制作
* 新增helper及grid文件
* 优化了animation动画

### 2.1版本
* 优化了变量，详见`_variables.scss`文件
* 将`_base.scss`改成`_core.scss`文件
* 不再提供css3前缀文件，推荐使用[autoprefixer](https://github.com/postcss/autoprefixer)来智能生成前缀（有grunt和gulp版本，有些客户端编译软件也集成了这个功能）。如果你还需要前缀文件请访问独立的[css3 scss](https://github.com/marvin1023/css3-scss)


## 如何使用
sandal和[sassCore](https://github.com/marvin1023/sassCore)一样，分核心文件和扩展文件两种。其中核心文件提供一些基础的样式和@mixin，%等方便调用；而扩展文件则提供一些模块的样式。

### 核心文件调用

第一种除提供基础功能外，会产生一份`reset`样式：

	@import "d:/sandal/core";

第二种不产生任何样式，只提供功能的调用：

	@import "d:/sandal/function";

### 扩展文件调用

根据需要调用，以`grid`为例：

	@import "d:/sandal/ext/grid";


## 文件简述

sandal包括两个集合文件（core，function）和三个文件夹（core，ext，components）。其中core文件夹中为核心基础文件，包括variables，media-queries，mixin，animation，reset；ext文件夹中是一些扩展文件，目前只包括font-face 和 svg 两种icons；components文件夹为组件，这里暂不介绍。

两个集合文件（core，function）导入的都是core中的文件，区别在于core除了提供基本功能之外还会生成一份reset样式，而function则只提供基本功能。至于ext中的文件则属于额外的一些模块扩展，可根据需求导入。

### core文件

#### variables
负责基础变量的文件，如常用的颜色，字体等变量。

#### media-queries
负责响应式宽度判断的文件。主要是对响应式布局的一些宽度判断，来自paranoida的[sass-mediaqueries](https://github.com/paranoida/sass-mediaqueries)。

#### mixin
负责功能方面的文件。这里我们大概分成三个部分，一个是混合部分即mixin（主要定义了一些常用的`flex`,`translate`等），一个是placeholder选择器部分即%，最后就是我们的function函数部分。常用的include及extend就是在这里定义的。

#### animation

提供四组简单实用动画：fade-in/out, shrink-in/out, up-in/out, down-in/out。默认不产生样式，通过include调用

### reset
在[normalize](http://necolas.github.io/normalize.css/)的基础上，根据目前我们大家的使用习惯进行了一些归零行动，及设置文字字体颜色。严格来说这并不是专门针对移动端的重置，而是ie8+的重置，因为考虑到有些是专门做移动端，而有些则是移动为先，再则重置的东西也比较少，所以就没有进一步砍掉。当然有代码洁癖的可以进一步优化。

### ext文件

#### helper

提供常用的基础class，如overlay, full-width等

#### grid

移动端的网格系统，分为row和col，具体使用参考[3分钟13行代码搭建sass版移动端网格系统](http://imweb.io/topic/570b33f806f2400432c139b3)

#### icons

分为绘制的icon和svg图标两种，可参考icons文件夹中的demo

![default icon svg](ext/icons/svg-icons.png)

**svg 图标调用**

从[icomoon](http://icomoon.io)提取了几个常用的svg图标，使用方法可参考demo中的demo.html，这里以home图标为例：

	<svg class="icon icon-home"><use xlink:href="icons.svg#icon-home"></use></svg>

如需改变颜色，可以通过css的fill属性来定义

	.icon-home{
		fill:#f00;
	}

最后可根据实际需求定义需要的icon， 然后使用。




