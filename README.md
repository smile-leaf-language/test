# 项目文档
## npm init -y   初始化一个package.json文件
## touch .gitignore webpack.config.js 。
## mkdir src&&touch index.html index.js
> ## 安装webpack依赖 npm install webpack webpack-dev-server --save-dev
> webpack 
> ## 安装babel依赖 npm install babel-core babel-loader babel-preset-es2015 babel-preset-react --save-dev
> .babelrc:设置转码规则和插件
   babel-cli工具，用于命令行转码。
   码需要调用Babel的API进行转码，就要使用babel-core模块。
  presets字段设定转码规则 比如：babel-preset-es2015（ES2015转码规则即ES6代码转为ES5）、babel-preset-react（react的jsx转码规则）、babel-preset-stage-0（es7的4个阶段中的第一个草案）


## lsof -i :8080 :查看8080端口号被哪些进程占用
## kill －9 6242 ：杀掉6242这个进程
## 有状态组件：Class App extends Component {}
## 无状态组件：const App = () => <h1>hello</h1>

## this.props:组件间的数据的传递，外部传入，内部通过this.props进行获取
## [组件名].propTypes :团队协作使用组件的时候首先看可通过此字段了解需要传哪些字段，字段的类型是什么，哪些是必须的 例如：[组件名].propTypes= [ url:React.propTypes.string, id:React.propTypes.number.isRequired ]
## [组件名].defaultProps:容错处理，当忘传某些字段的时候不会警告报错，而是走默认的值。[组件名].defaultProps ＝ ｛url：""，id：0｝  
## this.state:管理组件自己内部的数据，可定义初始状态
## this指针:es6中块级作用域this指向为undefined，es5中也会有指向错误，此时方法里的this.setState就会找不到报错，故须绑定this指针。
## 绑定this指针 第一种是在组件的constructor里面绑定this.handle = this.handle.band(this);第二种是用es6的箭头函数就不需要bind绑定了,但是需要配置stage－0的插件，安装本地依赖和配置.balbelrc,推荐这种；第三种是在input等的元素事件上调用方法是绑定例如：<input onClick={this.handle.bind(this)} type="text" />
## this.refs.［标识的属性名称］: 获取对应的虚拟DOM组件
## findDOMNode(this.refs.［标识的属性名称］): React的API，将获取的虚拟DOM组件转化为真实的DOM元素，即获取真实DOM元素标签
## this.props.children: 对外部传入的DOM元素进行获取
## React.children:React的API， 提供了五个方法（count、map、forEach、only、toArray），可以对this.props.children进行操作
# React生命周期 
## 第一个初始化创建阶段  getDefaultProps（es6中是 defaultProps）-> getInitialState（es6中是 this.state）-> componentWillMount（DOM元素渲染之前执行，只执行一次）-> render（DOM元素渲染，可以执行多次）-> componentDidMount（DOM元素渲染之后执行，只执行一次）
## 第二个运行中阶段 此过程可多次执行 (属性Props改变 componentWillRecieveProps)->状态State改变 ->shouldComponentUpdate 如果return false 状态不更新也就没改变不进行组件渲染 否则 return true-> componentWillUpdate -> render -> componentDidUpdate   
## 第三个卸载阶段  unmount componentWillUnmount （可有两种卸载方法  一种是定义状态destroy：false  操作设为true 返回null 不进行渲染 另一种是调用react的API进行DOM删除  封装remove方法 调用unmountComponentAtNode(element)的API ） ->结束

## React.children:API 提供了五个方法（count、map、forEach、only、toArray）