Get/Post
get请求发送一个包，包含http header和data,服务器响应
post请求发送两个包，先发送一个header,服务器响应100 continue,浏览器再发送data,服务器再响应
> ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
1、http是无状态的面向连接的协议，但是并不代表人家不能保持持续连接，它不是UDP协议(无连接)
2、从http/1.1起，默认都开始了keep-alive，如果想关闭默认的长链接，可以将connection设置为close
3、keep-alive不会永久保持连接，他有一个保持时间，一般都在服务器上设置
> ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
### 关于在浏览器地址栏输入url后的过程中，是先释放tcp连接还是先解析渲染页面
看它两建立的连接是长连接还是短链接？

### 状态码
```
400 -- 客户端请求语法错误
401 -- 未授权
403 -- 服务器收到请求，但是处理请求
404 -- 未找到对应资源
500 -- 服务器执行请求时发生错误
503 -- 服务器暂时无法处理请求
```
>~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
http1.0和http1.1的区别
1、默认使用了connection保持长连接
2、除了if-Modified-Since，引入了tag对应的if-Match-None
3、新增了24个状态码(409--表示请求的资源与当前资源的状态冲突)
(410 -- 表示服务器上的某个资源被永久性地删除)
4、**http1.0并不支持断点续传功能，http1.1引入了range头字段，允许只请求某个资源的某个部分（206），实现了断点续传功能