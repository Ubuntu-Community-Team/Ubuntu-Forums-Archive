---
title: "Problem with Zenoss install"
date: 2009-06-22
forum: Networking &amp; Wireless
---

### Post by btaylor101 on 2009-06-22
I have been trying to get Zenoss to install on my Ubuntu 8.04 server and the process seems to hang at > Setting up zenoss-stack (2.4.1-0) ...

I have also seen the following error below
> Error running /usr/local/zenoss/mysql/scripts/myscript.sh /usr/local/zenoss/mysql zenoss : ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/usr/local/zenoss/mysql/tmp/mysql.sock' (2)
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/usr/local/zenoss/mysql/tmp/mysql.sock' (2)
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/usr/local/zenoss/mysql/tmp/mysql.sock' (2)
Problem running post-install step. Installation may not complete correctly
 Error running /usr/local/zenoss/mysql/bin/mysql -h localhost -P 3307 -u root -pzenoss -S ../tmp/mysql.sock -e "CREATE DATABASE events;" : ERROR 2002 (HY000): Can't connect to local MySQL server through socket '../tmp/mysql.sock' (2)


I tried the latest install attempt as the root user and still no joy. I also removed the password from MySQL to stop a problem there. I read through the install doc from Zenoss' website and the installation is supposed to be easy enough, but I have found a way to make it more convulted than it should be. Any help would be greatly appreciated.

---

