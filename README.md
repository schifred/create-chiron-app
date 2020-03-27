## create-chiron-app

一个脚手架。

### 快速开始

```shell
npm install create-chiron-app -g
create-chiron myproject
# ? 请选择应用类型 pc 桌面应用
# ? 是否后台管理系统 Yes
# ? 应用名称 小青蛙
# ? 公司名称 小青蛙科技有限公司
# ? 侧边栏风格 dark
# ? 面包屑风格 complex
# ? 是否需要登录 Yes
# ? 是否启用调试模式 No
```

选择所要创建的应用类型、界面展示风格。项目中修改 publicPath 等。

### 依赖

* 构建工具使用 [umi 2](https://v2.umijs.org/zh/)。
* 组件库使用 [antd 4](https://ant.design/index-cn)。
* 图标使用 [react-icons](https://react-icons.netlify.com/#/icons/ai)。
* 请求库使用 [umi-request](https://github.com/umijs/umi-request)。
* 调试使用 [vconsole](https://github.com/Tencent/vConsole)，如 mac 电脑的钉钉环境。

### 配置项

meta.json 配置。

#### 展示配置项

```yaml
title: 应用名称
companyName: 公司名称
siderTheme: dark # 侧边栏风格，dark、light
breadcrumbsMode: simple # 面包屑风格，simple、complex
```

#### 功能配置项

```yaml
isAdmin: true # 是否后台管理系统
enableLogin: true # 是否包含登录功能
enableDebug: false # 启动调试，开发环境或线上环境带 debug=true 查询参数
```

### 接口约定

#### 通用接口

```yaml
success: true # 调用成功或失败 true, false
data: any # 响应数据
code: number # 响应 code。403 无权限，500，404 会自动跳转到相关页面
errorMessage: string # 错误信息
```

#### 分页接口

```yaml
list: array # 列表数据
total: number # 总条数
current: number # 当前页码
pageSize: number # 每页显示多少条
```

### 权限模型

由用户信息接口返回 authes 数组加以推断。

authes/NeedAuth 用于校验菜单权限。umirc#routes 配置添加 authes 数组，Routes 配置添加 NeedAuth，表示访问该菜单需要相关权限。

Components/Layouts/Authority 根据用户权限展示或隐藏子组件。
