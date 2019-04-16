# Session-Cookie-Demo
## 案例1.记录用户上次访问时间
* 需求：当用户哦第一次登陆的时候，提示：你是第一次访问，且记录该次访问时间，下一次访问的时候，获取上一次访问时间且展示出来
* 技术分析：会话技术，cookies jsp
### 步骤分析：
* 创建一个servlet：RemServlet路径：/rem
* 在servlet中：
  * 获取指定cookie 例如：名称为 lastTime
    * request.getCookies()
  * 判断cookie是否为空
     * 若为空：提示信息：第一次防卫
     * 如不为空：获取此cookie的value
     * 展示信息：你上次访问的时间
  * 将这次访问时间记录，写回浏览器
### jsp
* java serveer pages:java服务器界面
* 本质上是一个servlet,在html代码中嵌套java代码
* 运行在服务器端，处理请求，生成动态内容
* 对应的java和class文件在tomcat目录的work目录下，后缀名.jsp
* 执行流程：
  * 浏览器发送请求，访问jsp页面
  * 服务器接受请求，jspServlet会帮我们查找对应的jsp文件
  * 服务器将jsp页面翻译成java文件
  * jvm会将java编译成.class文件
  * 服务器运行class文件，生成动态内容
  * 将内容发送给服务器
  * 服务器组成相应信息发送给浏览器
  * 浏览器接收数据，解析展示
* jsp的脚本：
  * <%...%> java程序片段，生成在jsp的service方法中
  * <%=...%> 输出表达式，生成在jsp的service方法中，相当于在java中调用out.print()
  * <%!...%> 声明成员,
  
### 会话技术
* 当用户打开浏览器的时候，访问不同的资源，直到用户将关闭浏览器关闭可以认为这是一次会话。
* 作用：因为http协议是一个无状态的协议，他记录不了上次访问的内容。用户在访问的过程中难免会产生一些数据，通过会话计数就可以保存起来。
  * 例如：用户登录，验证码，购物车，访问记录
* 分类：
  * cookie:浏览器端的会话技术
  * session:服务器端的会话技术
#### cookie:
* cookie是由服务器生成，通过response将cookie写回浏览器(set-cookie)，保存在浏览器上，下一次访问，浏览器根据一定的规则携带不同的cookie（通过request的头：cookie）,服务器就可以接受cookie
* cookie的API:
  * new Cookie(String key,String value)
  * 写回浏览器：response.addCookie(Cookie c)
  * 获取cookie：Cookie[] request.getCooies()
  * cookie的常用方法：
    * getName()：获取cookie的key(名称)
    * getValue:获取指定cookie的值
