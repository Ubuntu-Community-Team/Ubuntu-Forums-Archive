---
title: "mythtv and mysql problems"
date: 2008-04-26
forum: Multimedia Software
---

### Post by josedb on 2008-04-26
i installed mythtv and mythubuntu packages in ubuntu 8.04 and followed the instructions, but when trying to connect database i get this:

Would you like to use Wake-On-LAN to retry database connections? [no]  
2008-04-26 12:23:57.975 Unable to connect to database!
2008-04-26 12:23:57.975 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-04-26 12:23:58.026 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-04-26 12:23:58.076 Cannot login to database?
2008-04-26 12:23:58.076 Cannot login to database?



ive searched over the internet but none solution was fine

---

### Post by duxducis on 2008-04-27
Try reinstalling mysql-server from [http://packages.ubuntu.com/hardy/all/mysql-server/download](http://packages.ubuntu.com/hardy/all/mysql-server/download). I had a very similar problem and aptitude was  not downloading them correctly.

---

### Post by spoky99 on 2008-04-30
I had the same problem solved in this way (I install ubuntu 8.04 and after all the mythtv packet using the normal repository)
The sistem display me more error like:
"no upnp backends"
"Cannot login to database?"
"ERROR 1045 (28000): Access denied for user 'mythtv'@'localhost' (using password: YES)"
ecc ecc

I install phpmyadmin and using it I don't found mysql user "mythtv" and the "mythconverg" database.
With phpmyadmin I create a new user "mythtv" and a new database "mythconverg" ghiving at the user mythtv access to mythconverg database with all privileges. My be is not the right solution but now it work :)

bye

---

