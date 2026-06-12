---
title: "Remote connection to domain fails"
date: 2009-06-18
forum: Networking &amp; Wireless
---

### Post by bugsbunny on 2009-06-18
I have an Ubuntu 8.04 server with 2 nerwork cards eth0 and eth1. I am using only eth0. The server is behind a 2-wire router. I have setup the router with the public IP addresses.

On the server I have setup an IP alias on eth0 as eth0:0. I have 3 domains which i will call foo1.com foo2.com and foo3.com. The server pc is assigned to a static public address on the router as 217.xx.xx.100 this same ip also used to setup the virtual host for foo1.com

> <VirtualHost 217.xx.xx.100:80>
ServerName foo1.com
ServerAlias [www.foo1.com](www.foo1.com)
ServerAdmin [email]me@foo1.com[/email]
DocumentRoot /var/www/foo1/
</VirtualHost>
I have also setup and applied an ssl certificate to 217.xx.xx.100:443.

Now eth0:0 is assigned to 217.xx.xx.101 and used as below


> <VirtualHost 217.xx.xx.101:80>
ServerName foo2.com
ServerAlias [www.foo2.com](www.foo2.com)
ServerAdmin [email]me@foo2.com[/email]
DocumentRoot /var/www/foo2/
</VirtualHost>

<VirtualHost 217.xx.xx.101:80>
ServerName foo3.com
ServerAlias [www.foo3.com](www.foo3.com)
ServerAdmin [email]me@foo3.com[/email]
DocumentRoot /var/www/foo3/
</VirtualHost>

When I am on the router I can access all the domains via the browser and can also get FTP, and ssh connection to the server. However when I leave the range of the server and connect to the net via another router, I loose ftp and ssh access to the server as well as not able to browse [www.foo1.com](www.foo1.com). However [www.foo2.com](www.foo2.com) and [www.foo3.com](www.foo3.com) I can browse.

---

