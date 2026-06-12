---
title: "Can't start mythbackend - mysql not running?"
date: 2008-01-04
forum: Mythbuntu
---

### Post by lingenfr on 2008-01-04
Last night, all was well. This evening, clicking Live TV brought no response. After a couple of attempts it said it couldn't connect to the backend. I had noticed last night in the jobs list what appeared to be a hung/disconnected live tv job. So when it would not start live tv this evening, I assumed that I had one or more hung jobs using the tuner. I ssh'd in and did a shutdown and restart. When it came back up, I got the frontend setup screens over and over. So, I ssh'd in and ran mybackend. I got the following:

--------------------------------
2008-01-04 20:08:30.489 Using runtime prefix = /usr
2008-01-04 20:08:30.503 New DB connection, total: 1
2008-01-04 20:08:30.504 Unable to connect to database!
2008-01-04 20:08:30.504 Driver error was [1/2002]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-01-04 20:08:30.555 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-01-04 20:08:30.605 Failed to init MythContext, exiting.
----------------------------------

When I check, there is not even a /var/run/mysqld directory. When I run mysqld I get:

---------------------
linghome@mythbox01:/var/run$ sudo mysqld
080104 20:10:07  InnoDB: Started; log sequence number 0 43655
080104 20:10:07 [ERROR] Can't start server : Bind on unix socket: No such file or directory
080104 20:10:07 [ERROR] Do you already have another mysqld server running on socket: /var/run/mysqld/mysqld.sock ?
080104 20:10:07 [ERROR] Aborting

080104 20:10:07  InnoDB: Starting shutdown...
080104 20:10:09  InnoDB: Shutdown completed; log sequence number 0 43655
080104 20:10:09 [Note] mysqld: Shutdown complete

_________________________-

I know next to nothing about mysql. What do I need to do to get this going again? Thanks.

---

### Post by lingenfr on 2008-01-06
I am not sure that I solved anything or diagnosed the problem, but I have started making headway toward bringing it back to life without a reinstall. As to the original problem, I think it relates to my HD filling up. Unfortunately, 300GB ain't what it used to be. Particularly when 1TB drives are selling for under $300. I did not delete anything from off the drive. I did try fooling around with deleting mysqld.pid and mysqld.sock from /var/run/mysqld/. I am not sure whether that help or not. I tried various methods of starting mysqld with no joy. This morning I did the following and got it going:

ssh into my master backend for the first session
sudo mysqld_safe
ssh into my master backend for the second session
sudo su mythtv
mythbackend

That seemed to work and I was able to connect with my frontend, so did a shutdown and restart and mysql, the backend and the frontend came up. Unfortunately, I've got no TV yet, but I am continuing to work on that.

I am really disappointed with the lack of help on this forum. The developers and more experienced users need to pitch in or I need to find a myth distribution that has a better following. I am going to start working on a new master backend machine and I am going to take the time to try knoppmyth and others before I go this way again. Hats off to folks on the distribution, but we still need some help. I am trying to do my part.

---

