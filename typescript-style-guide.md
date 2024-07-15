# TypeScript编码规范

## 1 前言

本文档在[JavaScript编码规范](./javascript-style-guide.md)的基础上针对TypeScript编码作进一步的补充，目标是使团队成员 TypeScript 代码风格保持一致，容易被组内其他人理解和维护。

## 规范
1) [建议]非必要情况下不能使用 any
```ts
// bad
const data: any = {
    name: 'name',
    age: 18,
    address: 'beijing',
}

interface ListItem {
    name: string
    age: number
    address: string
}

// good
const data: ListItem = {
    name: 'name',
    age: 18,
    address: 'beijing',
}
```
如果一个对象有多层嵌套，并且数据过多，不确定性太大。可以使用 AnyObject 来代替 any。

```ts
type AnyObject = Record<string, any>
```

2) [建议]接口 API 返回值使用 interface 进行声明

```ts
interface Params {
    id: string
    name: string
}

interface ListItem {
    name: string
    age: number
    address: string
}

export function getListData(params: Params): Promise<ListItem[]> {
    return request({
        url: '/people/list',
        params,
    })
}
```
3) [建议]不要在全局命名空间内定义类型/值
4) [建议]为函数，接口，枚举类型和类使用JSDoc风格的注释
5) [建议]使用arrow函数代替匿名函数表达式
6) 