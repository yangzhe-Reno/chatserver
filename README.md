# chatserver
## 功能介绍：
- 接入层：在muduo库基础上构建，使用userConnMap保存用户的连接信息，为提升并发性能，使用分段加锁
- 业务逻辑层：处理基于json的应用协议，实现了用户登录、注册和添加好友、单聊、群聊等功能。
- 存储层：基于MySQL数据库实现，设计了用户表，好友关系表，群聊表，离线消息表等，并设计了数据库连接池，复用数据库连接，来提高存储性能。
- 水平扩展：可以在启动Nginx作为网关，同时启动多个chatserver进程，通过Nginx的TCP长连接负载均衡器将连接均衡分配给chatserver进程，同时使用Redis发布订阅功能对跨进程的消息进行转发。

