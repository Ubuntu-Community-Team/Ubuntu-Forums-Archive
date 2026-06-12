---
title: "MythTv Backend ip problems"
date: 2007-05-17
forum: Multimedia &amp; Video
---

### Post by awinner on 2007-05-17
Hi

I have mythtv setup on fiesty, everything works fine except of one thing. When the computer initially boots and i run mythtv and try to watch tv, i get an error message that it cannot connect to the backend is the ip correct?

The odd thing is that this doesnt happen everytime, sometimes it boots up fine and i can watch tv, when i cant, i drop into command line and do a /etc/init.d/mythtv-backend restart and then tv works. I have checked using ps and mythtv-backend is always running. the ip set for the backend is 127.0.0.1, machine ip is 192.168.1.100

What am i doing wrong?

TIA

---

### Post by newlinux on 2007-05-18
When it doesn't work, take a look at your logs. Run mythfrontend from the terminal and watch its output. Also look at:

/var/log/mythtv/mythbackend.log

Maybe there are some clues in there. This is a combined frontend/backend, correct? When you restart the backend, does it tell you that no backend was running?

---

### Post by awinner on 2007-05-19
thanks for the reply, mythbackend.log shows nothing abnormal, mythbackend is definitely running because if i /etc/init.d/mythtv-backend start ,it tells me backend is running and to use restart instead. 

I havent solved the problem but i appear to have a workaround. In mythtv setup i have not told it to use 192.168.1.100 instead of 127.0.0.1 and now the tv works fine without a restart.

---

### Post by mwacky on 2007-10-01
I also having the same problem as above, same message when I try to start mythtv backend.  But when I try to restart mythtv:

```
mwacker@Barney:~$ sudo /etc/init.d/mythtv-backend start
mythbackend already running, use restart instead.
mwacker@Barney:~$ sudo /etc/init.d/mythtv-backend restart
Restarting MythTV server: mythbackend No /usr/bin/mythbackend found running; none killed.
.
.
```

I did nothing to configure the backend, I installed directly from sudo apt-get install mythtv.

---

### Post by josesanders on 2007-11-26
I'm having the same problem.  Did you find a solution?  I've checked the IP addresses, and everything is okay.  I even tried changing the IP address to localhost, since this is currently just a combined frontend/backend system.  If I try to run the command:

$ sudo netstat -tap|grep LISTEN

I don't see any service listening on port 6543, as I believe that the mythtv server is supposed to be listening on.

Any ideas?

---

### Post by josesanders on 2007-12-11
I partially solved the problem.  MythTV wasn't able to start up because I'm using LVM, and I needed to change the permissions for the nfslockfile.  I don't know what this means, but I changed the permissions, and the backend starts up, although not automatically.  For some reason, I have to manually restart it every time the computer reboots.  I still can't get the remote frontend systems to connect, but at least now, the local frontend is working, and I can see that it is listening on the right ports.

---

### Post by tc7 on 2008-02-16
I had a similar issue changing the recording directory. Initially I thought this was because I was specifying another file system.

The server process wasn't starting up (and of course the client could connect).
All became clearer by "tailing" the logs, eg:

cd /var/log/mythtv
tail *.log

then run mythtv-setup from another terminal and observe what happens after you exit mythtv-setup.

I was getting the following message:
2008-02-17 00:11:31.351 Enabled verbose msgs:  important general
/<path>/recordings/nfslockfile.lock: No such file or directory
Unable to open lockfile!
Be sure that '/recordings' exists and that both
the directory and that file are writeable by this user.

permissions on recordings and lock file was fine - but I was missing an "x" permission on one of the parent directories for 'other' (mythtv user).

problem solved!

---

### Post by jubei52 on 2008-03-12
I just installed mythv and I can't connect to my backend at all.  It is a backend/frontend machine with everything one one box.

I am using Dapper Drake 6.06.  FOr somereason, my backend server won't start.  this is my .log file:

marcozd@marcozd-ubuntu:~$ more /var/log/mythtv/mythbackend.log
2008-03-12 19:26:47.603 Using runtime prefix = /usr
QSettings: error creating /root/.qt
QSettings::sync: filename is null/empty
2008-03-12 19:26:47.749 New DB connection, total: 1
2008-03-12 19:26:47.779 Unable to connect to database!
2008-03-12 19:26:47.801 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-03-12 19:26:47.894 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-03-12 19:26:47.977 Failed to init MythContext, exiting.
2008-03-12 20:07:51.658 Using runtime prefix = /usr
QSettings: error creating /.qt
QSettings::sync: filename is null/empty
2008-03-12 20:07:51.875 New DB connection, total: 1
2008-03-12 20:07:51.978 Connected to database 'mythconverg' at host: localhost
2008-03-12 20:07:51.995 Current Schema Version:


Any ideas would be great as I am very new to linux and myth TV.

---

### Post by josesanders on 2008-03-24
It seems that MythTV is unable to connect to the mysql database.  Try logging in manually with the following command:

$ mysql -u mythtv -p

MythTV keeps the mysql password in the file:
 ~/.mythtv/mysql.txt

---

