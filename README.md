# 前端开发说明

##  开发环境搭建

#### 1、安装Node.js

Node.js安装包下载地址：
http://nodejs.cn/download/

根据自己的操作系统下载合适的安装包，通常安装包会自动添加所需的环境变量，可以通过下面的命令进行检查

```
node -v
```
如果显示版本号即表示安装成功

#### 2、包管理工具 npm

安装node.js后会自动安装包管理工具npm，可输入下面命令检查是否安装成功

```
npm -v
```
如果显示版本号即表示安装成功

#### 3、安装yarn

Yarn是更为先进的包管理工具，可以视为npm的替代品

输入下面命令进行全局安装

```
npm install -g yarn
```
安装完成后输入下面命令检查是否安装成功

```
yarn --version
```
如果显示版本号即为安装成功

#### 4、项目初始化

在前端开发目录(包含有package.json的目录)下打开命令行，运行下面的命令：

```
yarn install
```
该命令会下载开发所需的所有依赖，安装成功后即可开始进行开发

## 开发环境的使用

#### 1、开发工具

开发工具可使用 Visual Studio Code 或者 WebStorm

前者开源且轻量，可通过安装扩展来实现更多的功能，自定义化程度高

后者需要付费，不过功能十分强大

两者对Vue都有较好的支持

#### 2、启动调试服务器

运行命令：

```
yarn dev
```
该命令会在本地打开调试服务器，通过 http://localhost:9940 进行访问

在修改代码后，该调试服务器会自动编译并热部署，浏览器可以直接看到修改后的结果，非常方便。

如果要修改端口号，需要修改/config/index.js文件，将dev中的port属性修改为新的端口号，然后重启调试服务器。

#### 3、启动mock服务器

运行命令：
```
yarn mock
```
该命令会打开mock数据服务器，可以用来模拟后端的数据，从而达到前后端分离的目的。

接口逻辑需要放到/mock/api目录下，该目录下的js都会被扫描到，可仿照已有的用例来添加

通过 http://localhost:9941 进行访问

如果要修改mock服务器的端口号，需要修改两个地方：

- package.json: scripts中的mock命令，最后的数字改为新的端口号
- /config/index.js: dev中找到proxyTable属性，里面定义了请求的转发，target地址需要改为新的端口号

#### 4、前端编译

前端开发完毕后，需要生成编译文件才能供后端使用，编译的命令为：
```
yarn build
```
生成的文件在整个app模板的/app/static和/app/templates目录下，该位置是固定的，不要对配置进行修改。

## 开发使用到的技术

### Vue
响应式前端框架，同时用到了vue-router、vuex

文档地址： https://cn.vuejs.org/

### ElementUI
饿了么出品的Vue组件库，里面内置了很多基础并常用的组件

文档地址：http://element.eleme.io/#/zh-CN

### lodash
包含了很多实用函数的js库，处理数组、对象时经常能用到

直接通过全局变量“\_”进行使用，例如:
```js
_.map(list, value => {
  return value.id
})
```

文档地址：https://lodash.com/

### axios
RESTful请求库，在该模板下通过this.$http即可直接调用，例如:
```js
this.$http.get(url)
```

文档地址：https://www.npmjs.com/package/axios

### less
css预处理語言，支持变量、嵌套等功能，可在/src/assets/less下编写less文件，也可以在.vue文件的style标签中使用# web
