---
title: "mysql-admin and lampp"
date: 2008-12-09
forum: Networking &amp; Wireless
---

### Post by pavel989 on 2008-12-09
I tried to run mysql-admin (just to see what its like, i dont even really know how to use mysql yet...)and it gave me error nr. 2002 - 

something about not being able to lock onto /var/run/mysqld/mysql.sock

and im guessing this has something to do with the fact that im running mysql from Lampp. 

is there something i need to fix, or is the problem unrelated to me running mysql through lampp?

---

### Post by Ayuthia on 2008-12-09
Have you checked to see if mysql is running:
```
ps -ef|grep mysql
```
If it only comes back with a grep line and the line does not start with mysql then mysql has not been started.  You will need to start it:
```
sudo /etc/init.d/mysql start
```

---

### Post by pavel989 on 2008-12-09
```

root@pavel-server:~# ps -ef|grep mysql
root      5390  5372  0 17:25 pts/0    00:00:00 grep mysql

root@pavel-server:~# /opt/lampp/lampp start
Starting XAMPP for Linux 1.6.8a...
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Starting MySQL...
XAMPP: Starting ProFTPD...
XAMPP for Linux started.

root@pavel-server:~# ps -ef|grep mysql
root      5447     1  0 17:27 pts/0    00:00:00 /bin/sh /opt/lampp/bin/mysqld_safe 
[INDENT]--datadir=/opt/lampp/var/mysql 
--pid-file=/opt/lampp/var/mysql/pavel-server.pid[/INDENT]

nobody    5477  5447  0 17:27 pts/0    00:00:00 /opt/lampp/sbin/mysqld[INDENT]--basedir=/opt/lampp 
--datadir=/opt/lampp/var/mysql  
--user=nobody 
--pid-file=/opt/lampp/var/mysql/pavel-server.pid  
--skip-external-locking 
--port=3306 
--socket=/opt/lampp/var/mysql/mysql.sock[/INDENT]

root      5504  5372  0 17:27 pts/0    00:00:00 grep mysql

```

that was the output for the commands, right when i booted my machine. I changed the spacing and stuff to make it look nicer.

my point is, does it matter which mysql server is running so long as it sits on 3306?

-------------------------------------------------------------------------
I noticed that lampp uses a specific socket. i told mysql-admin to use it. Works fine now!

---

### Post by Ayuthia on 2008-12-09
I am not for sure, but it looks like you have the right one running.  I am not for sure what mysql_safe is supposed to do, but the mysqld is the one that you want running.

---

