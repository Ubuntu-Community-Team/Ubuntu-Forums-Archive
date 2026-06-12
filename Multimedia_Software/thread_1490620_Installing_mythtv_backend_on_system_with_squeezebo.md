---
title: "Installing mythtv backend on system with squeezeboxserver using mysql"
date: 2010-05-22
forum: Multimedia Software
---

### Post by mmcmonster on 2010-05-22
I have squeezeboxserver running to control my [Logitech Squeezebox]("http://www.logitechsqueezebox.com/").  I am now trying to install mythtv backend on the same system.

When I install mythtv backend and run the setup application (System->Administration->MythTV Backend Setup) and leave the default host name and database name, it returns to the first screen with the error message: "Myth could not connect to the database. Please verify your database settings below.  Required fields are marked with an asterisk (*)."

```
$ ps -ef | grep mysql
117      20315 20304  0 May21 ?        00:00:13 /usr/sbin/mysqld --defaults-file=/var/lib/squeezeboxserver/cache/my.cnf
mysql    23711     1  0 09:34 ?        00:00:03 /usr/sbin/mysqld
mmcmonster  24869 24818  0 13:46 pts/2    00:00:00 grep mysql

```It looks like squeezeboxserver is running mysql with some options so that mythtv isn't able to create the proper database?

So then I removed squeezebox, but this didn't help.

```

mysql -u root mysql
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

```

---

### Post by petatkinson on 2010-05-26
I'm having a similar problem too and have been asking questions on the same subject.I remember having a similar problem in an earlier version of Ubuntu and it was down to the MySQL settings database and the port Myth was trying to connect on.

---

