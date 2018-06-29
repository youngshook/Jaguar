# Jaugar
基于 Ruby on Rails 和 [Faslane](https://github.com/fastlane/fastlane) 的移动客户端 CI 平台（后端）  
前端在这项目中 https://github.com/thierryxing/Falcon

## 安装环境

### 操作系统
因为iOS编译及打包需要依赖 Xcode，所以需要 Mac OS 10.9+ 系统，有条件的公司可以直接上Mac Pro，当然 Mac Mini 也是可以的，但是建议高配版+SSD。

### Ruby&Rails
Jaguar本身是基于 Ruby on Rails 开发的，需要 Ruby2.3环境（2.4+理论上也可以，但是没有测试过），Rails使用的是 5.1.6 版本。

### 数据库
Jaguar使用的是 MySQL5.6 版本

### Redis and Sidekiq
自动化异步任务全部跑在 Sidekiq上，Sidekiq 本身需要 Redis 作为存储，所以需要安装 Redis。


## 安装指南

### Ruby
由于 Mac 系统自带的Ruby是2.0.*版本的，比较老，而 Jaugar 使用的 Rails 5.1 版本依赖 Ruby 2.2+，所以需要手动安装一下 2.3 版本。
这里推荐使用 RVM 进行安装。

1. 安装 RVM：

> curl -sSL https://get.rvm.io | bash -s stable

2. 安装 Bundler：

> gem install bundler

3. 安装 Gem 依赖：

> bundle install


### 初始化

1. 构建本地配置文件：

> cp .env .env.local

2. 初始化数据库和表结构
> RAILS_ENV=production rake db:create 
> RAILS_ENV=production rake db:migrate
