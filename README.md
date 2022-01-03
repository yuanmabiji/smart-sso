# smart-sso
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](http://opensource.org/licenses/MIT)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/a466350665/smart-sso/pulls)
[![GitHub stars](https://img.shields.io/github/stars/a466350665/smart-sso.svg?style=social&label=Stars)](https://github.com/a466350665/smart-sso)
[![GitHub forks](https://img.shields.io/github/forks/a466350665/smart-sso.svg?style=social&label=Fork)](https://github.com/a466350665/smart-sso)

QQ交流群：454343484🈵、769134727

## 简述
    smart-sso使用当下最流行的SpringBoot技术，基于OAuth2认证授权协议，为您构建一个易理解、高可用、高扩展性的分布式单点登录应用基层。

## 相关文档
- [smart-sso单点登录（一）：简介](https://blog.csdn.net/a466350665/article/details/54140411)
- [smart-sso单点登录（二）：部署文档](http://blog.csdn.net/a466350665/article/details/79628553)
- [smart-sso单点登录（三）：App登录支持](https://blog.csdn.net/a466350665/article/details/109742638)
- [smart-sso单点登录（四）：引入redis支持分布式](https://blog.csdn.net/a466350665/article/details/109388429)

## 组织结构

```lua
smart-sso
├── smart-sso-client -- 客户端依赖包
├── smart-sso-client-redis -- 客户端依赖包，分布式redis支持
├── smart-sso-demo -- 客户端
├── smart-sso-server -- 服务端
```

## 单点登录原理
![smart_sso_login.jpg](smart_sso_login.jpg)
#### 注意点：
1. 图中第4步生成的cookie（TGC）的domain是server.smart-sso.com,此时只有浏览器访问server.smart-sso.com才会带着TGC过去，即访问demo.smart-sso.com等TGC是不会带过去的，此时在server.smart-sso.com单点登录后，然后直接打开demo.smart-sso.com，此时怎样才能做到直接登录的状态呢？
关键点在于重定向，即访问demo.smart-sso.com时，此时重定向到server.smart-sso.com，所以浏览器自然会带着TGC到server.smart-sso.com服务端啦，然后在server.smart-sso.com服务端判断TGC相关逻辑，如果已经登录，那么产生一个授权code，授权code作为查询参数再重定向到demo.smart-sso.com，然后demo.smart-sso.com再根据code去server.smart-sso.com验证即可（之后步骤笔记未完待续）。

## 单点退出原理
![在这里插入图片描述](https://img-blog.csdnimg.cn/20201118165835197.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2E0NjYzNTA2NjU=,size_16,color_FFFFFF,t_70#pic_center)


## 效果展示
### 单点登录页
![在这里插入图片描述](https://img-blog.csdnimg.cn/20201030163204421.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2E0NjYzNTA2NjU=,size_16,color_FFFFFF,t_70#pic_center)

### 服务端登录成功页
![在这里插入图片描述](https://img-blog.csdnimg.cn/20201030163112313.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2E0NjYzNTA2NjU=,size_16,color_FFFFFF,t_70#pic_center)

### 客户端登录成功页
![](https://img-blog.csdnimg.cn/20201020163349855.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2E0NjYzNTA2NjU=,size_16,color_FFFFFF,t_70#pic_center)