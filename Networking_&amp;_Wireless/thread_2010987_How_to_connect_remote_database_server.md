---
title: "How to connect remote database server"
date: 2012-06-26
forum: Networking &amp; Wireless
---

### Post by xinchao on 2012-06-26
Hi everybody!

I want to create two servers: Web server and database server. Web server using database provided by db server

I use Virtual box to do that.

+ Web server installed: ssh, apache
IP: 192.168.56.102

+ DB server: installed: ssh, mysql server
IP: 192.168.56.101
I create use mysqluser with password dbserver

In web server I try to login: mysql -u mysqluser -p -h 192.168.56.101
When I enter password 'dbserver'. This error occured: 
ERROR 2003 (HY000): Can't connect to MySQL server on '192.168.56.101' (113)

I try to: telnet 192.168.56.101 3306
telnet: connect to address 192.168.56.101: No route to host
telnet: Unable to connect to remote host: No route to host

I try to ping 192.168.56.101. It's ok.
I try to ssh from web server to database server. It's ok.

Please tell me how to routing for web server can connect database server throught port 3306 (MySQL)

Sorry for English not good :D. Thank you very much.

---

