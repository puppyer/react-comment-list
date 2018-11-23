## 使用
    

### Node

```sh
npm install
node server.js
```


## 改变端口

```sh
PORT=3001 node server.js
```

## 功能

* 显示评论列表
* 提交表单
* 支持markdown格式

## 文件说明

* server.js:相当于一个简易的服务器，用来获取和保存数据
* comments.json:这里的数据库使用JSON文件来代替,文件用于存储评论相关的信息
* public:用于书写HTML、CSS、JS

## 组件规划说明

在这个页面，一共有四个组件，结构如下
- CommentBox
  - CommentList
    - Comment
  - CommentForm

## 操作步骤

1. 先表示出该评论页面的大致轮廓，并添加一些样式

2. 使用props获取数据
  
   - 数据应该显示到Comment组件中，所以在使用Comment组件的时候传入一些属性，在Comment组件中通过props来获取数据

3. 使支持Markdown格式

   - 使用第三方库remarkable，这里使用script来引入remarkable

4. 声明一个JSON数据，然后读取该数据并渲染到页面
   - 声明一个变量data来存储JSON数据，然后在CommentBox组件中作为属性值来传给子组件使用；而在子组件CommentList中，将this.props.data作为属性值又传给其子组件Comment来使用

5. 把写死的数据换成从后台获取动态数据

   - <CommentBox url="/api/comments" /> ，在server.js文件中，写明了/api/comments路径下不同的请求所做的事情
   - 在CommentBox组件中，将data变量存储在state中，而通过从后台获取数据来更新state。在CommentList组件上，用this.state.date作为其属性值来供子组件使用