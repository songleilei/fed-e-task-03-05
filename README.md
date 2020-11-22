# fed-e-task-03-05

## Vue 3.0 性能提升主要是通过哪几个方面体现的

- 响应式系统升级（proxy）
  - 可以监听动态新增的属性
  - 可以监听删除的属性
  - 可以监听数组的索引和 length 属性
- 编译优化 （标记和提升所有的静态根节点，diff 的时候只需要对比动态节点内容）
  - Fragments
  - 静态提升
  - Patch flag
  - 缓存事件处理函数
- 源码体积的优化
  - 移除不常用的 API
  - Tree-shaking

## Vue 3.0 所采用的 Composition Api 与 Vue 2.x 使用的 Options Api 有什么区别

- Composition Api
  - 基于函数
  - 灵活，易于组合，复用
  - 更好的类型推导，容易集合 TypeScript
- Options Api
  - 包含一个描述组件选项的对象
  - 开发复杂组件，同一个功能代码被分散到不同选项中
  - 不利于复用

## Proxy 相对于 Object.defineProperty 有哪些优点

- proxy 对象的性能本身就比 defineProperty 好
- 代理对象可以拦截属性的访问、赋值、删除等操作
- 不需要初始化的时候遍历所有的属性
- 有多层属性嵌套，只有访问某个属性的时候，才会递归处理下一级的属性
- 监听动态新增属性、监听删除属性、监听数组的索引和 length 属性

## Vue 3.0 在编译方面有哪些优点

编译优化 （标记和提升所有的静态根节点，diff 的时候只需要对比动态节点内容）

- Fragments
- 静态提升
- Patch flag
- 缓存事件处理函数

## Vue 3.0 响应式系统的实现原理

Vue 3.0 使用 ES6 的 Proxy 进行数据响应化。

- 初始化阶段

  ​ 通过 reactive() 方法将数据转化成 Proxy 对象

- 依赖收集阶段

  ​ 通过 effect() 、track() 等函数收集依赖

- 响应阶段

  ​ 通过 trigger 触发更新

```javascript
/* 建立响应式数据 */
function reactice(obj) {}

/* 声明响应函数cb(依赖响应式数据) */

function effect(cb) {}

/* 依赖收集 */
function track(target, key) {}

/* 触发更新 */
function trigger(target, key) {}
```
