---
title: "Am I missing an obvious step in my MythTv install?"
date: 2007-02-01
forum: Multimedia &amp; Video
---

### Post by Tdonohue on 2007-02-01
Hopefully, someone browsing here recognizes an obvious step I am missing.  I am unable to complete the installation of Mythtv using the tutorial found here:

[https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop]("http://https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop")

I've added myself to the mythtv group.  but running 

mythtv-setup

```
QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-02-01 20:39:00.225 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-02-01 20:39:00.277 Database not open while trying to save setting: Language
2007-02-01 20:39:00.279 Unable to connect to database!
tim@tim-laptop:~$ 0.279 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-02-01 20:39:00.329 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-02-01 20:39:05.213 Unable to connect to database!
2007-02-01 20:39:05.213 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-02-01 20:39:05.266 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-02-01 20:39:05.318 Failed to init MythContext, exiting.

```

throws out a bunch of errors (the above is just a few), then a blue screen comes up about not being able to connect to the Mysql database.  I follow the troubshooting instructions at the bottom of the tutorial, that seems to describe the exact problem I'm having, but it complains about my syntax being wrong.

1)  "mythtv" doesn't appear under the users (system>admin>Users & Groups), but when I try to create it, it says it exists.  I've tried to login    User=mythtv     password=myth  and it doesn't work.

For anyone willing to help, Let me know what commands I can try and I will post the results.

Thanks in advance for your suggestions

---

### Post by Tdonohue on 2007-02-01
I must have had a typo in commands I was using, but I managed to get the setup going and the front end to come up.  I got warnings during the setup that the backend was not connected to the Mysql database.  

```
tim@tim-laptop:~$ sudo /etc/init.d/mythtv-backend restart
Password:
Restarting MythTV server: mythbackendNo /usr/bin/mythbackend found running; none killed.
.
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
.
tim@tim-laptop:~$ ps -p `cat /var/run/mythtv/mythbackend.pid`
  PID TTY          TIME CMD
tim@tim-laptop:~$ 

```

Still don't know how to connect it.  I have installed Phpmyadmin, and I've got that configured, but I don't know how or if that can help me with this issue.

Appreciate any ideas!

Thank you

---

### Post by Unisted on 2007-02-02
I've been having problems with Myth for a few weeks now and it kept on giving me the backend not connected message too.

However, last night I took inspiration from this post:

[http://www.ubuntuforums.org/showthread.php?t=349592](http://www.ubuntuforums.org/showthread.php?t=349592)

Basically, I completely removed myth-frontend, backend, database and any other bits you may have as well as removing sql-server.

Then followed this guide: [http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

BUT, after installing mysql again I logged into mysql to check it was working - the problems I was having was that it required the root password which I had changed previously but thought it was re-set during **complete** removal of SQL-Server... it wasn't!

The run the rest of the guide.

My installation seems fine, but saying that when I exit it says "Cannot Connect to Backend" but I think it is because I commented out a line in the mysql config document from a previous guide!

Persistance is the key! The forums are an amazing source of information and there are many many posts on this subject.

Good luck!

Edit: This went wrong for me too! [http://ubuntuforums.org/showthread.php?t=347086](http://ubuntuforums.org/showthread.php?t=347086)

---

