# LoadBalancingTree
负载均衡，硬件负载均衡，软件负载均衡


![](https://i.imgur.com/uhHIQbG.png)

<pre>
硬件负载均衡
      F5
        F5负载均衡器是应用交付网络的全球领导者F5 Networks公司提供的一个负载均衡器专用设备，F5 BIG-IP LTM 的官方名称叫做本地流量管理器，可以做4-7层负载均衡，具有负载均衡、应用交换、会话交换、状态监控、智能网络地址转换、通用持续性、响应错误处理、IPv6网关、高级路由、智能端口镜像、SSL加速、智能HTTP压缩、TCP优化、第7层速率整形、内容缓冲、内容转换、连接加速、高速缓存、Cookie加密、选择性内容加密、应用攻击过滤、拒绝服务(DoS)攻击和SYN Flood保护、防火墙—包过滤、包消毒等功能。

        以下是F5 BIG-IP用作HTTP负载均衡器的主要功能：
 
　　       ①、F5 BIG-IP提供12种灵活的算法将所有流量均衡的分配到各个服务器，而面对用户，
            只是一台虚拟服务器。

　　       ②、F5 BIG-IP可以确认应用程序能否对请求返回对应的数据。假如F5 BIG-IP后面的某一
            台服务器发生服务停止、死机等故障，F5会检查出来并将该服务器标识为宕机，从而不
            将用户的访问请求传送到该台发生故障的服务器上。这样，只要其它的服务器正常，用
            户的访问就不会受到影响。宕机一旦修复，F5 BIG-IP就会自动查证应用已能对客户请
            求作出正确响应并恢复向该服务器传送。

　　       ③、F5 BIG-IP具有动态Session的会话保持功能。

　　       ④、F5 BIG-IP的iRules功能可以做HTTP内容过滤，根据不同的域名、URL，将访问请求
             传送到不同的服务器
</pre>

<pre>
软件负载均衡：
      目前比较流行的就三类软件负载均衡，LVS、Nginx和HAProxy。用的最多的还是LVS和Nginx这两种
      
      LVS
         平时我们说的LVS是Linux Virtual Server。这当然是基于Linux的开源软件了，这就意味着它是免费的。它基本上能支持所有应用，因为lvs工作在4层，
      所以它可以对几乎所有应用做 负载均衡，包括http、数据库、聊天室等等。同时，若跟硬件负载均衡相比它的缺点也不容忽视，LVS要求技术水平很高，操作
      上也比较复杂，配置也很繁 琐，没有赖以保障的服务支持，稳定性来说也相对较低（人为和网络环境因素更多一些）
      
      Nginx
         在这里，我们介绍Nginx就需要跟LVS来对比了。LVS是工作在第四层，对网络的依赖性相对较大。然而Nginx是工作在第七层，对于网络的依 赖性就小的多。
      与LVS相比，Nginx的安装和配置也相对简单一些，另外测试方面也更简单，主要还是因为对网络依赖性小的缘故。Nginx有一点不好的 就是应用要比LVS少。一
      般我们做软件负载均衡的时候，通常会先考虑LVS，但是遇到比较复杂的网络环境时，用LVS可能会遇到很多麻烦，不妨就考虑尝试 一下Nginx
      
      HAProxy
         使用HAProxy的人非常少，对其了解的也不多。通过官方的了解，HAProxy提供高可用性、负载均衡以及基于TCP和HTTP应用的代理，支 持虚拟主机，它是
      免费、快速并且可靠的一种解决方案。HAProxy特别适用于那些负载特大的web站点，这些站点通常又需要会话保持或七层处理。（据说 是可以工作在4-7层的。）
      并且它的运行模式使得它可以很简单安全的整合进您当前的架构中，同时可以保护你的web服务器不被暴露到网络上。
</pre>

<pre>
软硬件负载均衡的优缺点对比：
      硬件负载均衡：
           优点：能够直接通过智能交换机实现,处理能力更强，而且与系统无关，负载性能强更适
                用于一大堆设备、大访问量、简单应用

           缺点：成本高，除设备价格高昂，而且配置冗余．很难想象后面服务器做一个集群，但最
                关键的负载均衡设备却是单点配置；无法有效掌握服务器及应用状态

      软件负载均衡器
           优点：基于系统与应用的负载均衡，能够更好地根据系统与应用的状况来分配负载。这对
                于复杂应用是很重要的，性价比高，实际上如果几台服务器，用F5之类的硬件产品
                显得有些浪费，而用软件就要合算得多，因为服务器同时还可以跑应用做集群等。

           缺点：负载能力受服务器本身性能的影响，性能越好，负载能力越大
</pre>


![](https://i.imgur.com/yhJNclJ.png)


![](https://i.imgur.com/7RfkOms.png)

<pre>
大型网站系统集群架构
</pre>

<pre>
负载均衡算法：

      常见的6中负载均衡算法：  
           1）轮询
           2）随机
           3）源地址哈希
           5）加权轮询
           6）加权随机
           7）最小连接数

      Nginx 5种负载均衡算法：
           1）轮询
           2）weight
           3) ip_hash
           5) fair
           6) url_hash

      dubbo负载均衡算法：
           1）随机
           2）轮询
           3）最少活跃调用数
           5）一致性hash
</pre>