---
title: "mythbackend pooped itself"
date: 2009-05-26
forum: Mythbuntu
---

### Post by MonsterMaxx on 2009-05-26
Normally when this happens I know how to fix it, but that's in RedHat distros. Everything is just enough differnt in ubuntu that nothing I know how to do works.

It was running just fine and it locked up. Reboot and it's hosed.

I'm willing to bet it's corrupted the database, but I can't find anything in the logs about it or docs on fixing it in ubuntu.

It's totally down now, not even a reboot gets it running. When it boots up I get the blue 'language selection' screen.


Bright ideas on how to fix it?



BTW, is this forum running extremely slow today?

---

### Post by tgm4883 on 2009-05-26
> **MonsterMaxx said:**
> Normally when this happens I know how to fix it, but that's in RedHat distros.

I'm willing to bet it's corrupted the database, but I can't find anything in the logs about it or docs on fixing it in ubuntu.

It's totally down now, not even a reboot gets it running. When it boots up I get the blue 'language selection' screen.


Bright ideas on how to fix it?



BTW, is this forum running extremely slow today?

Post the logs here for the backend.

You can also enable a daily optimize/repair db job in MCC

---

### Post by MonsterMaxx on 2009-05-26
Allright, I'm sorry, but like I said, things I could do in Fed/myth don't work in mythbuntyu.
Where do I find the backend logs? They aren't under the system logs...that I can find.

And what's with this forum? It was so slow last night all it would do is time out, today, every move is taking minutes.
It's never been like this for me,

---

### Post by tgm4883 on 2009-05-26
Logs are in /var/log/mythtv/

Don't know why the forum is slow for you, it's pretty quick here.

---

### Post by MonsterMaxx on 2009-05-27
ya know what, I think this machine is totally screwed. It can't even manage a simply copy/paste of the log file.

This is a fast machine and a copy/paste has brought it to it's knees.

Too bad, I kinda liked ubuntu, oh, well

---

### Post by MonsterMaxx on 2009-05-27
ok then.

I gotta be taking stupid pills or something today, I can't get it to attach normally (not a valid file type) so I try to compress it, no freeking app that I can find, ok, change the extension to .zip and upload. That crashes firefox. Ok, open with a text editor and copy paste. That crashes both the text editor and firefox.
????

This machine does NOTHING but mythbackend. I haven't even got all the stuff installed that was running in Fedora/Centos. Ugh. Frustrating. And now it's totally shat itself.

---

### Post by MonsterMaxx on 2009-05-27
Here's some of it.


QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-05-27 15:40:47.418 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2009-05-27 15:40:47.469 Cannot login to database?
2009-05-27 15:40:47.470 Cannot login to database?

Cannot login to database?

Would you like to configure the database connection now? [yes]  
[console is not interactive, using default 'yes']
Database host name: [localhost]  
[console is not interactive, using default 'localhost']
Should I test connectivity to this host using the ping command? [yes]  
[console is not interactive, using default 'yes']
Database non-default port: [0]  
[console is not interactive, using default '0']
Database name: [mythconverg]  
[console is not interactive, using default 'mythconverg']
Database user name: [mythtv]  
[console is not interactive, using default 'mythtv']
Database password: [ZUYagcq4]  
[console is not interactive, using default 'ZUYagcq4']
Unique identifier for this machine (if empty, the local host name will be used):  
[console is not interactive, using default '']
Would you like to use Wake-On-LAN to retry database connections? [no]  
[console is not interactive, using default 'no']
2009-05-27 15:40:47.639 Unable to connect to database!
2009-05-27 15:40:47.647 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-05-27 15:40:47.714 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2009-05-27 15:40:47.765 Cannot login to database?
2009-05-27 15:40:47.766 Cannot login to database?

Cannot login to database?

Would you like to configure the database connection now? [yes]  
[console is not interactive, using default 'yes']
Database host name: [localhost]  
[console is not interactive, using default 'localhost']
Should I test connectivity to this host using the ping command? [yes]  
[console is not interactive, using default 'yes']
Database non-default port: [0]  
[console is not interactive, using default '0']
Database name: [mythconverg]  
[console is not interactive, using default 'mythconverg']
Database user name: [mythtv]  
[console is not interactive, using default 'mythtv']
Database password: [ZUYagcq4]  
[console is not interactive, using default 'ZUYagcq4']
Unique identifier for this machine (if empty, the local host name will be used):  
[console is not interactive, using default '']
Would you like to use Wake-On-LAN to retry database connections? [no]  
[console is not interactive, using default 'no']
2009-05-27 15:40:47.935 Unable to connect to database!
2009-05-27 15:40:47.943 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-05-27 15:40:48.010 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2009-05-27 15:40:48.061 Cannot login to database?
2009-05-27 15:40:48.062 Cannot login to database?

Cannot login to database?

Would you like to configure the database connection now? [yes]  
[console is not interactive, using default 'yes']
Database host name: [localhost]  
[console is not interactive, using default 'localhost']
Should I test connectivity to this host using the ping command? [yes]  
[console is not interactive, using default 'yes']
Database non-default port: [0]  
[console is not interactive, using default '0']
Database name: [mythconverg]  
[console is not interactive, using default 'mythconverg']
Database user name: [mythtv]  
[console is not interactive, using default 'mythtv']
Database password: [ZUYagcq4]  
[console is not interactive, using default 'ZUYagcq4']
Unique identifier for this machine (if empty, the local host name will be used):  
[console is not interactive, using default '']
Would you like to use Wake-On-LAN to retry database connections? [no]  
[console is not interactive, using default 'no']
2009-05-27 15:40:48.235 Unable to connect to database!
2009-05-27 15:40:48.243 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-05-27 15:40:48.312 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2009-05-27 15:40:48.363 Cannot login to database?
2009-05-27 15:40:48.364 Cannot login to database?

Cannot login to database?

Would you like to configure the database connection now? [yes]  
[console is not interactive, using default 'yes']
Database host name: [localhost]  
[console is not interactive, using default 'localhost']
Should I test connectivity to this host using the ping command? [yes]  
[console is not interactive, using default 'yes']
Database non-default port: [0]  
[console is not interactive, using default '0']
Database name: [mythconverg]  
[console is not interactive, using default 'mythconverg']
Database user name: [mythtv]  
[console is not interactive, using default 'mythtv']
Database password: [ZUYagcq4]  
[console is not interactive, using default 'ZUYagcq4']
Unique identifier for this machine (if empty, the local host name will be used):  
[console is not interactive, using default '']
Would you like to use Wake-On-LAN to retry database connections? [no]  
[console is not interactive, using default 'no']
2009-05-27 15:40:48.543 Unable to connect to database!
2009-05-27 15:40:48.551 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-05-27 15:40:48.652 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2009-05-27 15:40:48.703 Cannot login to database?
2009-05-27 15:40:48.766 Cannot login to database?

Cannot login to database?

Would you like to configure the database connection now? [yes]  
[console is not interactive, using default 'yes']
Database host name: [localhost]  
[console is not interactive, using default 'localhost']

---

### Post by tgm4883 on 2009-05-27
Try this

> If you are having problems connecting to your mysql database, you can perform the following to reconfigure it: 1. sudo dpkg-reconfigure mysql-server-5.0 (pay attention to the root password you set, you will need it for the next step) 2. sudo dpkg-reconfigure mythtv-database 3. sudo dpkg-reconfigure mythtv-common

---

### Post by MonsterMaxx on 2009-05-28
the page sluggishness is showing a long delay transfering data from  yui.yahooapis.com

very long long long time waiting for that


And those three commands got the job done. Big thanks.


FYI, my gut feel is that it's mythweb that's corrupting the database. I'm usually watching tv, maybe it's recording in the background, and then make a mythweb request and that's when things go wonky (on rare occations.)

---

### Post by tgm4883 on 2009-05-29
That should be fine.  Try doing a full memory test.

---

