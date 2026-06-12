---
title: "MythTv Kicking my butt!!!!"
date: 2007-08-23
forum: Multimedia &amp; Video
---

### Post by xhero0 on 2007-08-23
Ok call me a noob... but this is kicking my ***.. I keep on getting this error......

```
2007-08-22 21:10:37.478 Database not open while trying to save setting: Language
2007-08-22 21:10:37.479 Unable to connect to database!
2007-08-22 21:10:37.479 Driver error was [1/2002]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-08-22 21:10:37.534 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-08-22 21:10:42.568 Unable to connect to database!
2007-08-22 21:10:42.568 Driver error was [1/2002]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-08-22 21:10:42.627 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-08-22 21:10:42.682 Failed to init MythContext, exiting.
Restarting MythTV server: mythbackend No /usr/bin/mythbackend found running; none killed.

```

this is just a snipet of the end of the same error msg....

any one know how to get this running?!?!?!

thanx!

joe...

---

### Post by hangthedj on 2007-08-23
this means that mysql is not running

try running 
```
sudo /etc/init.d/mysql start
```

---

### Post by xhero0 on 2007-08-23
I got this:

```
sudo: /etc/init.d/mysql: command not found
```

I am gonna try to reinstal it again

---

### Post by xhero0 on 2007-08-23
OK I further than ever before I can smell victory.. but....

when I use the frontend to watch the tv it says that my tuner is in use. and in the status it says that the card is unavailable, and it said something like have I ran mythfilldatabase of something like that....

thanx!


joe...

---

### Post by hangthedj on 2007-08-23
make sure your getting mysql-server and mysql-server5.0 not just mysql-client.

---

### Post by xhero0 on 2007-08-23
mysql 5.0          <check>
mysql server     <check>

---

### Post by hangthedj on 2007-08-23
I'm no expert on MythTv, i don't have a tuner, i use it to organize movies, but you have to run mythtv-setup, and setup your main ip, and what tuner card, and other information to get channels and stuff, and after you do that it will ask if you want to run mythfilldatabase, for your channel list.  Sorry i couldn't be more help :)

---

### Post by newlinux on 2007-08-23
what install guide did you follow? I strongly recommend following the guides in the community docs:

[https://help.ubuntu.com/community/MythTV_Feisty](https://help.ubuntu.com/community/MythTV_Feisty)

If you didn't, I would even recommend uninstalling and starting over.

Other than it would be more helpful to know about how you installed it. How you setup your tuner, what tuner card you are using. etc.

---

