---
layout:     post
title:      dialog
subtitle:    "初识html-dialog"
date:       2019-05-18
author:     Booleen
header-img: img/tag-bg-o.jpg
catalog: true
tags:
    - html
---

## 前言

html5总有一些有意思的标签，最新了解到一个直接生成对话框或其他交互式组件的标签，即`dialog`

虽然了解到它的兼容性不太好，但是支持chrome49及以上啊，在公司的项目中说不定可以用上，就去搜索一下相关的知识点。


## 兼容性

caniuse上截图如下：

![兼容性](/img/article_img/dialog_index.jpg)


## 基本用法

- open

`规定 dialog 元素是活动的，用户可与之交互。
表示这个对话框可以进行互动.
open未设置该属性时，不应向用户显示该对话框。`

简单示例：
```html
<dialog open>
  <p>hello,everyone! I'm dialog .</p>
</dialog>
<!-- 显示如下图 -->
```

![示例1](/img/article_img/dialog_1.png)

```html
<dialog>
  <p>hello,everyone! I'm dialog .</p>
</dialog>
<!-- 将不会显示 -->
```
- showModal()

`模式化的显示这个对话框， 并且将会至于所有其他对话框的顶层（屏蔽其他对话框的交互）。 
可选传入类型为Element 或者 MouseEvent 的参数， 用来定义对话框的显示位置。`

示例：

html:
```html
  <dialog>
        <p>hello,everyone! I'm dialog .</p>
        <button id="closeDialog">关闭</button>
    </dialog>
```
js:

```javascript
var dialog = document.getElementsByTagName("dialog")[0],
    openDialog = document.getElementById("openDialog"),
    closeDialog = document.getElementById("closeDialog");

    openDialog.onclick = function () {
        dialog.showModal();
    }

    closeDialog.onclick = function () {
        dialog.close();
    }
```
css样式：

```css
    dialog:not([open]) {
        display: none;
    }

    dialog {
        display: block;
        position: absolute;
        left: 0;
        right: 0;
        width: -webkit-fit-content;
        height: -webkit-fit-content;
        color: black;
        margin: auto;
        border-width: initial;
        border-style: solid;
        border-color: initial;
        border-image: initial;
        padding: 1em;
        background: white;
    }

    dialog::backdrop {
        position: fixed;
        top: 0;
        right: 0;
        bottom: 0;
        left: 0;
        background: rgba(0, 0, 0, 0.8);
    }
```
![示例2](/img/article_img/dialog_2.png)

- close()

`关闭对话框。 可选传入类型为{domxref("DOMString")}}的参数，用来更新对话框的returnValue。`

示例如上showModel()：

tips:
`样式可以自定义的，在标签内就跟写hmtl一样就好啦`
下面是我写的demo截图。

![示例3](/img/article_img/dialog_3.png)

其实就是一个简单的模态窗，简单实用。

—— Booleen 后记于 2019.05