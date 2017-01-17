# node_12306
##适用场景：
已经确定了火车的车次和时间（最好提前3-4天），但是没有座位了。想抢有座位的（只能抢别人的退票了，几天内一般都会有人退票）。
##使用方法：
  * 克隆代码到本地``` git clone https://github.com/hongrunhui/node_12306.git ``` 
  * 在当前文件夹终端``` npm install ```安装依赖
  * ```node main.js```，第一次运行会要求输入信息并且存入config.json，以后再次运行只会读取config.json中的数据，不会要求再次输入。如：
  ![image](https://cloud.githubusercontent.com/assets/9162319/22015721/2bb4a91e-dcde-11e6-98da-5753bc6d238f.png)
  * ```node main.js -r```可以重写config.json(重新输入信息)。
  * 车次(```train_num```字段)可以输入多个车次，用|分开，如K123|K234(前提这些车次都在同一线路上)。
  
##注意：
  * 要使用邮件功能前提是要去邮箱设置里开启smtp;也可以用邮箱授权码代替，这种方式更安全。具体可以见[wiki](https://github.com/hongrunhui/node_12306/wiki/%E9%82%AE%E7%AE%B1%E8%AE%A4%E8%AF%81%E9%94%99%E8%AF%AF%E8%A7%A3%E5%86%B3%E5%8A%9E%E6%B3%95)
  * 针对有人提出程序可能会报错退出的问题，这里建议使用[pm2](http://pm2.keymetrics.io/)来启动```main.js```,具体步骤：
 	  * ```npm install pm2 -g```全局安装pm2
 	  * ```[sudo] pm2 start main.js```启动程序（linux可能会需要管理员权限）
    * ```[sudo] pm2 list```列出当前程序的运行情况
    * ```[sudo] pm2 stop```停止程序
    * 大家可以放到自己的服务器上面去运行，这样全天24小时都可以监听你的车次还有没有票，并及时给你发邮件。
  * 有人提出自动抢票下单支付功能，这个我以后会想办法去实现。
  * [博客地址](http://www.cnblogs.com/hongrunhui/p/6284192.html)

##更新：
  * 0.0.0.4
    * 车站代码查询改为车站拼音查询
  * 0.0.0.3
    * 增加学生票查询
    * 增加给其他人发邮件
    * 查询不到信息时自动跳过进入下一次查询
    * 修复JSON数据报错bug
  * 0.0.0.2
    * 可在命令行输入信息
    * 配置文件与主文件分离
    * 支持同一线路多车次监听
    * 修复一些bug
  * 0.0.0.1
    * 实现基本功能

##声明
  * 本程序最适合监听那些一张票都没有的车次(或者无座多，硬座/软座/硬卧/软卧无的车次)，通过本程序可以24小时监听车次是否会多出余票，并及时发送邮件通知个人(可以使用```pm2```部署在自己的服务器上或24小时开着电脑运行实现24小时监听)
  * 对于有特殊需求的可以自己修改代码或者咨询我。