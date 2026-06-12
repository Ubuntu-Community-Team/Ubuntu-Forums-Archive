---
title: "[mythbuntu 7.10 liveCD] no mythconverg database"
date: 2008-04-12
forum: Mythbuntu
---

### Post by MaaxLil on 2008-04-12
Hello, 
 
I use a mythbuntu 7.10 downloaded on  mythbuntu.org  today, as a live CD.

After clicking on 'Live CD Frontend Icon' and entering the parameters given in /etc/mythtv/mysql.txt into the 'Mythbuntu live session configuration' dialog box , I couldn't connect by clicking on test connection button.

I tried to figure out ...

First ... mysql wasn't running ?? I launched it by checking the unchecked case beside the Database  server Mysql Icon in the services settings application.
Second, I finally noticed I had no mythconverg database.

```
ubuntu@ubuntu:~$ mysql -u root -p mythconverg
Enter password: 
ERROR 1049 (42000): Unknown database 'mythconverg'

```

```

ubuntu@ubuntu:~$ mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 11
Server version: 5.0.45-Debian_1ubuntu3-log Debian etch distribution

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.
mysql> show databases
    -> ;
+--------------------+
| Database           |
+--------------------+
| information_schema | 
| mysql              | 
+--------------------+
2 rows in set (0.00 sec)

```

Did I miss something ?
Thx.

---

### Post by laga on 2008-04-12
mysql and mythbackend are not supposed to run off the live disk. You need an existing backend and mysql server somewhere on your network.

Running mysqld and mythbackend off the CD is possible, but not directly supported and requires some hacking.

---

### Post by tgm4883 on 2008-04-14
Also, you need to make sure that on your existing backend you have the mysql service enabled.  You can do this in mythbuntu-control-centre

---

