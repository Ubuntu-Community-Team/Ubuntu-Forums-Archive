---
title: "2003 - Can't connect to MySQL server on 'IP address' (10061)"
date: 2006-07-09
forum: Networking &amp; Wireless
---

### Post by honiball on 2006-07-09
I have just installed Ubuntu 6.06 LAMP server.  I have confirmed that MySQL is up and running.  
However, when I try and connect to the Ubuntu Linux MySQL server from a Windows XP client using Navicat, or MySQL Admin, I get the error message "2003 - Can't connect to MySQL server on 'IP address' (10061)".  
Telnet also gives an error "Could not open connection to the host, on port 3306".  
I have not made any changes to the Linux server, or to MySQL on it, and have not even changed the MySQL root password.  
I can ping the Linux server from the XP client without a problem.

Assistance in solving my problem will be greatly appreciated.

Thanks.

---

### Post by DoorGunner on 2006-07-09
It looks like a problem with Microsoft

Check these out

[http://www.experts-exchange.com/Databases/Mysql/Q_20737391.html](http://www.experts-exchange.com/Databases/Mysql/Q_20737391.html)

[http://dev.mysql.com/doc/refman/5.0/en/can-not-connect-to-server-on-windows.html](http://dev.mysql.com/doc/refman/5.0/en/can-not-connect-to-server-on-windows.html)

Im sorry i dont really have experience with this problem. :oops:

---

### Post by ryant on 2006-07-09
You need to give access to the mysql user.  first login to that server from local host and add users to the mysqldb.

[http://dev.mysql.com/doc/refman/5.0/en/adding-users.html](http://dev.mysql.com/doc/refman/5.0/en/adding-users.html)

---

