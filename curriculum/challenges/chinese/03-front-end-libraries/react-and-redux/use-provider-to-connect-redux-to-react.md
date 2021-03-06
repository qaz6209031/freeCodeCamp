---
id: 5a24c314108439a4d4036144
title: 使用 Provider 连接 Redux 和 React
challengeType: 6
forumTopicId: 301435
---

# --description--

在上一挑战中，你创建了 Redux store 和 action，分别用于处理消息数组和添加新消息。下一步要为 React 提供访问 Redux store 及发起更新所需的 actions。`react-redux`包可帮助我们完成这些任务。

React Redux 提供的 API 有两个关键的功能：`Provider`和`connect`。你会在另一个挑战中学`connect`。`Provider`是 React Redux 包装 React 应用的 wrapper 组件，它允许你访问整个组件树中的 Redux`store`及`dispatch（分发）`方法。`Provider`需要两个 props：Redux store 和 APP 应用的子组件。用于 APP 组件的`Provider`可这样定义：

```jsx
<Provider store={store}>
  <App/>
</Provider>
```

# --instructions--

此时，编辑器上显示的是过去几个挑战中所有代码，包括 Redux store、actions、`DisplayMessages`组件。新出现的代码是底部的`AppWrapper`组件，这个顶级组件可用于渲染`ReactRedux`的`Provider`，并把 Redux 的 store 作为 props 传入。接着，渲染`DisplayMessages`为子组件。完成这些任务后，你会看到 React 组件渲染到页面上。

**注意：** React Redux 在此可作全局变量，因此你可通过点号表示法访问 Provider。利用这一点，编辑器上的代码把`Provider`设置为常量，便于你在`AppWrapper`渲染方法中使用。

# --hints--

`AppWrapper`应渲染。

```js
assert(
  (function () {
    const mockedComponent = Enzyme.mount(React.createElement(AppWrapper));
    return mockedComponent.find('AppWrapper').length === 1;
  })()
);
```

`Provider`组件应传入相当于 Redux store 的`store`参数。

```js
(getUserInput) =>
  assert(
    (function () {
      const mockedComponent = Enzyme.mount(React.createElement(AppWrapper));
      return getUserInput('index')
        .replace(/\s/g, '')
        .includes('<Providerstore={store}>');
    })()
  );
```

`DisplayMessages`应渲染为`AppWrapper`的子组件。

```js
assert(
  (function () {
    const mockedComponent = Enzyme.mount(React.createElement(AppWrapper));
    return (
      mockedComponent.find('AppWrapper').find('DisplayMessages').length === 1
    );
  })()
);
```

`DisplayMessages`组件应渲染 h2、input、button、`ul`四个元素。

```js
assert(
  (function () {
    const mockedComponent = Enzyme.mount(React.createElement(AppWrapper));
    return (
      mockedComponent.find('div').length === 1 &&
      mockedComponent.find('h2').length === 1 &&
      mockedComponent.find('button').length === 1 &&
      mockedComponent.find('ul').length === 1
    );
  })()
);
```

# --solutions--

