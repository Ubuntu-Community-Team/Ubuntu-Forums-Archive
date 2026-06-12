---
title: "Cannot login to database (mythTV)"
date: 2009-08-03
forum: Mythbuntu
---

### Post by hundred1906 on 2009-08-03
Tearing my hair out here. MythTV crashed out with a database error. Since then I have been trying to correct/restart/rebuild with increased levels of frustration.

Where I am now is that setup opens with a "No UPnP Backends Found" report. and after a couple of screens worth of configuration stuff finally gives me a "Cannot Login to Database (OK?)" error box. Actually it is not OK! Especially as I am pretty sure I am entering the correct password.

There are more than several posts on this but the general impression is that this is not an easy problem to get past - something to do with it being best not to enter a root name or password somewhere in the process. Frankly this is getting very frustrating.

I have had enough of trying to find socket names and the other half-dozen things you have to know in order to follow many of the guides - so I would like to hit the problem with something heavy and no-messing final.

What I need is to completely strip out all vestiges of MySQL and MythTV and to start over - but without entirely rebuilding my underlying desktop system.

Can anyone help and restore my sanity?

---

### Post by newlinux on 2009-08-04
Before you try to start over...

If you are sure you are entering the correct password, have you verified the mysql server and mythbackend server are running when you try to connect to them? Have you tried  connecting to the mysql server separately and looking in the mythbackend log?

Also, you may need to run a repair on your database, but you'll need to be able to connect to it to do that.

---

### Post by hundred1906 on 2009-08-04
Thanks. I would be sure I am entering the correct password - if I was getting in. As it is I am entering the one that is showing on the setup screen, the same as is in the mysql.txt file. It could be I am using the wrong user name - I have lost track of whether it should be blank, or Root or mythtv or something else entirely.

I don't know how to ensure the server and backend are running, nor how to connect to the server seperately.

I did run a repair on the mythtvconverg database (using mysqlrepair as I recall) resulting in a page or more of OK's and no reported problems. To do that I had to enter the password and also the name of the socket file. How I got the file name was through another utility as advised from a forums page somewhere or another. However this did not fix the underlying database problem and my subsequent messing about has undoubtably made a simple fault worse.

Hence my desire to clear everything down and build up from the beginning.

---

### Post by newlinux on 2009-08-04
what does:

```

ps aux | grep mythbackend 

```
return on the machine with your master backend? This will tell you if the backend is running.

the username for connecting the myth database should "mythtv" and this should be in your mysql.txt file as well...

What about looking in the backend log (in /var/log/mythtv/)?

As far as cleaning up and starting over not sure what the best complete way to do it is - that's something I've never actually done.

How did you install myth (via apt, mythbuntu-control-center, separate packeges, installing mythbuntu-desktop, installing the mythbuntu distro, etc.).

---

### Post by hundred1906 on 2009-08-04
I installed mythbuntu onto Ubuntu 9.04. It ran fine for weeks and I was just getting to really like it. When the database crashed I was hammering it a bit using the web interface to extract recording files while it was also recording.

From your code I get:

 ps aux | grep mythbackend
mythtv    3666  0.1  2.1  86652 22208 ?        Dsl  06:51   1:03 /usr/bin/mythbackend --daemon --logfile /var/log/mythtv/mythbackend.log --pidfile /var/run/mythtv/mythbackend.pid
trevor   21556  0.0  0.0   3340   796 pts/0    R+   20:00   0:00 grep mythbackend

The mythbackendlog file is 212Mb bytes long. Below I cut material from the top only. There is also a seperate ...Log1 file which is earlier but not quite so large. The password shown is exactly as I expect it.

[console is not interactive, using default 'Culture-Base']
Should I test connectivity to this host using the ping command? [yes]  
[console is not interactive, using default 'yes']
Database non-default port: [0]  
[console is not interactive, using default '0']
Database name: [mythconverg]  
[console is not interactive, using default 'mythconverg']
Database user name: [mythtv]  
[console is not interactive, using default 'mythtv']
Database password: [csTre5JK]  
[console is not interactive, using default 'csTre5JK']
Unique identifier for this machine (if empty, the local host name will be used):  
[console is not interactive, using default '']
Would you like to use Wake-On-LAN to retry database connections? [no]  
[console is not interactive, using default 'no']
2009-08-04 07:10:03.070 Unable to connect to database!
2009-08-04 07:10:03.173 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on 'Culture-Base' (111)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-08-04 07:10:03.348 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2009-08-04 07:10:03.462 Cannot login to database?
2009-08-04 07:10:03.550 Cannot login to database?

Cannot login to database?

Would you like to configure the database connection now? [yes]  
[console is not interactive, using default 'yes']
Database host name: [Culture-Base]  
[console is not interactive, using default 'Culture-Base']
Should I test connectivity to this host using the ping command? [yes]  
[console is not interactive, using default 'yes']
Database non-default port: [0]  
[console is not interactive, using default '0']
Database name: [mythconverg]  
[console is not interactive, using default 'mythconverg']
Database user name: [mythtv]  
[console is not interactive, using default 'mythtv']
Database password: [csTre5JK]  
[console is not interactive, using default 'csTre5JK']
Unique identifier for this machine (if empty, the local host name will be used):  
[console is not interactive, using default '']
Would you like to use Wake-On-LAN to retry database connections? [no]  
[console is not interactive, using default 'no']
2009-08-04 07:10:04.706 Unable to connect to database!
2009-08-04 07:10:04.825 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on 'Culture-Base' (111)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-08-04 07:10:04.982 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2009-08-04 07:10:05.093 Cannot login to database?
2009-08-04 07:10:05.141 Cannot login to database?

---

