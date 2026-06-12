---
title: "[SOLVED] Is mythbackend runnin?"
date: 2008-02-22
forum: Mythbuntu
---

### Post by volkswagner on 2008-02-22
How can I verify mthbackend is running on my slave machine?

I have to start it manually to be recognized by my master backend.  I seems in the logs it only registers as a client.  When I start the backend manually it registers as a slave.

---

### Post by newlinux on 2008-02-22
I use monit([http://www.mythtv.org/wiki/index.php/Status_Monitoring_How_To](http://www.mythtv.org/wiki/index.php/Status_Monitoring_How_To)), and can check if it is running by viewing the monit status web page. But you can ssh into your slave machine and you should be able to tell if it is running by looking for the mythbackend process.

```

pgrep mythbackend

```
should return a process id if it is running

---

### Post by volkswagner on 2008-02-22
```
pgrep mythbackend
```

Tried the above.  I was greeted with a returned prompt.  So it is not running.  What do I need to do to get it to start automagically?  Shouldn't it always start?  This is an advanced install of mythbuntu 7.10 slave BE/FE i386.  I am not sure if it ever did auto start.

---

### Post by newlinux on 2008-02-22
When I pgrep for mythbackend I get a process ID when it is running, so it probably isn't.
I guess to be sure you could always do:
```

sudo /etc/init.d/mythtv-backend start

```

If it is already running it will tell that it was, otherwise it will start...

I don't use mythbuntu, but the myth install from packages autostarts by default, I believe. Is it just not starting after reboots? Check your logs, it may be starting and failing. If you don't find anything in the logs, we can make sure your runlevels are setup to autostart mythtv-backend, but I really think this is done by default.

---

### Post by volkswagner on 2008-02-22
On the slave machine I don't get a process ID when

```
pgrep mythbackend
```

 I do however get a process id when I run the above on the master.

When I try to access the log on the slave "bedroom" I get..

> eric@Bedroom:~$ tail -f /var/log/mythtv/mythbackend.log
Database error was:
Can't connect to MySQL server on '192.168.1.107' (101)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-02-22 16:35:02.353 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-02-22 16:35:02.404 Failed to init MythContext, exiting.

The ip of master is correct.  What I have to do is exit frontend >From XFCE menu select >Mythtv-Backend-Setup> then close setup, don't even run mythfilldatabase and then all is well.

What do you think.

If I try the following on the slave..

```
sudo /etc/init.d/mythtv-backend start
```

I get...

```
mythbackend already running, use restart instead.
```

So I try to restart...

```
eric@Bedroom:~$ sudo /etc/init.d/mythtv-backend restart
Restarting MythTV server: mythbackend No /usr/bin/mythbackend found running; none killed.
```

Seems to me the system thinks backend is running yet it may not be.

---

### Post by volkswagner on 2008-02-22
I performed my abnormal restart.  Here are some past backend logs.  Any thoughts.  I am sure the Master backend is running.  The password and ip are correct.  

```
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime FROM jobqueue j, recorded r WHERE j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.inserttime, j.chanid, j.id;
No error type from QSqlError?  Strange...
2008-02-19 20:42:00.586 Unable to connect to database!
2008-02-19 20:42:00.591 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.1.107' (113)

QSqlQuery::exec: database not open
```


```
stream: start_time: 0.289 duration: 10.054 bitrate=5439 kb/s
2008-02-18 20:01:06.967 AFD: Opened codec 0x815e580, id(MPEG2VIDEO) type(Video)
2008-02-18 20:01:06.989 AFD: Opened codec 0x815e980, id(MP2) type(Audio)
[mpeg2video @ 0xb7389ce8]warning: first frame is no keyframe
[mpeg2video @ 0xb7389ce8]ac-tex damaged at 35 17
[mpeg2video @ 0xb7389ce8]Warning MVs not available
2008-02-18 22:01:56.362 commflag: Commercial Flagging Finished: Dance War: Bruno vs. Carrie Ann recorded from channel 1008 at Mon Feb 18 20:00:00 2008: 0 commercial break(s)
2008-02-18 22:01:56.413 JobQueue: Commercial Flagging Finished, 0 break(s) found.
2008-02-18 22:01:56.416 MythSocket(81a1020:-1): writeStringList: Error, called with unconnected socket.
2008-02-18 22:01:56.419 Preview Error: Run() file not local: '/var/lib/mythtv/recordings/1008_20080218200000.mpg'
```



```
Database error was:
Can't connect to MySQL server on '192.168.1.107' (101)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-02-12 19:51:14.634 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-02-12 19:51:14.685 Failed to init MythContext, exiting.
```


Question:  What command allows more output of the log.  I know Ctrl+c makes it quit.

---

### Post by volkswagner on 2008-02-23
Wow how little I know.  

I installed monit.  I see the config instructions yet I do not know what I need to change in the config file.  I do not have a mail server.  What edit hints can somone offer.

> set daemon  30
set logfile /var/log/monit.log
set mailserver smtp.mydomain.com
set mail-format
 { from: [email]monit@bao.mydomain.com[/email] }
set alert [email]root@mydomain.com[/email]  # Send alert to system admin on any event
set httpd port 2812 and
    allow ash.mydomain.com
    allow 10.0.0.90
    allow 127.0.0.1
    allow haze.mydomain.com
    allow admin:monit     # user 'admin' with password 'monit'

What do I set the mail stuff to?  How do I access the web interface?

---

### Post by newlinux on 2008-02-23
I commented out the mail stuff, as I'm not interested in the mail (I commented out the lines between set logfile and set httpd). I allowed each computer on my domain to view the web page by IP address.

You can then go see it by going to

[http://machineIP:2812](http://machineIP:2812) 

If you leave the port as default username admin, password monit if you leave it as default. You can only view from machines listed in the allow statements.

My mythbackend portion looks like:

```

check process mythbackend with pidfile /var/run/mythtv/mythbackend.pid
 group mythtv
 start program = "/etc/init.d/mythtv-backend restart"
 stop program  = "/etc/init.d/mythtv-backend stop"
 depends on mysql

```

I took out the port portions from the template, but I don't remember why. It didn't work properly or something.

I run monit in daemon mode. Just remember to stop monit when you need to stop the backend to make configuration changes, or it will just start the backend up again when you don't want it to :)

```

sudo /etc/init.d/monit stop 

```
to stop the daemon

---

### Post by volkswagner on 2008-03-19
I am still trying to debug this bugger.  I see different errors now in the backend log.

Not sure what to do.

Here is the log after a system restart.  In this state the system complains mythbackend is already running if I try to restart it.  No process id is given if I pgrep.  If I run the restart command twice it will restart.

Backend log after restart:
```
2008-03-19 18:33:59.904 Using runtime prefix = /usr, libdir = /usr/lib
2008-03-19 18:34:00.029 Empty LocalHostName.
2008-03-19 18:34:00.043 Using localhost value of Bedroom
2008-03-19 18:34:00.079 Testing network connectivity to 192.168.1.107
2008-03-19 18:34:00.203 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2008-03-19 18:34:00.234 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
SSDP::PerformSearch - did not write entire buffer.
2008-03-19 18:34:00.304 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
SSDP::PerformSearch - did not write entire buffer.
...........................................................................
2008-03-19 18:34:02.609 UPnPautoconf() - No UPnP backends found
2008-03-19 18:34:02.813 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [yes]
[console is not interactive, using default 'yes']
Database host name:
[console is not interactive, using default '']
Should I test connectivity to this host using the ping command? [yes]
[console is not interactive, using default 'yes']
Database non-default port: [0]
[console is not interactive, using default '0']
Database name: [mythconverg]
[console is not interactive, using default 'mythconverg']
Database user name: [mythtv]
[console is not interactive, using default 'mythtv']
Database password: [*editPrivate*]
[console is not interactive, using default '*editPrivate*']
Unique identifier for this machine (if empty, the local host name will be used):
[console is not interactive, using default '']
Would you like to use Wake-On-LAN to retry database connections? [no]
[console is not interactive, using default 'no']
2008-03-19 18:34:03.745 Could not open settings file /home/mythtv/.mythtv/mysql.txt for writing
2008-03-19 18:34:03.814 Deleting UPnP client...
2008-03-19 18:34:03.826 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2008-03-19 18:34:04.465 Failed to init MythContext, exiting.
```

Log after running backend setup (no changes, just to stop/start backend)


```
2008-03-19 19:04:50.523 Using runtime prefix = /usr, libdir = /usr/lib
2008-03-19 19:04:50.766 Empty LocalHostName.
2008-03-19 19:04:50.767 Using localhost value of Bedroom
2008-03-19 19:04:50.769 Testing network connectivity to 192.168.1.107
2008-03-19 19:04:50.844 New DB connection, total: 1
2008-03-19 19:04:50.868 Connected to database 'mythconverg' at host: 192.168.1.107
2008-03-19 19:04:50.870 Closing DB connection named 'DBManager0'
2008-03-19 19:04:50.889 Connected to database 'mythconverg' at host: 192.168.1.107
2008-03-19 19:04:50.892 New DB connection, total: 2
2008-03-19 19:04:50.918 Connected to database 'mythconverg' at host: 192.168.1.107
2008-03-19 19:04:50.923 Current Schema Version: 1214
Running as a slave backend.
2008-03-19 19:04:50.934 mythbackend: MythBackend started as a slave backend
2008-03-19 19:04:50.942 New DB connection, total: 3
2008-03-19 19:04:50.957 Connected to database 'mythconverg' at host: 192.168.1.107
2008-03-19 19:04:52.671 Main::Registering HttpStatus Extension
2008-03-19 19:04:52.674 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-03-19 19:04:52.675 Enabled verbose msgs:  important general
2008-03-19 19:04:53.683 Connecting to master server: 192.168.1.107:6543
2008-03-19 19:04:53.685 Connected successfully
2008-03-19 19:05:00.941 mythbackend: Running housekeeping thread
```


Questions:

```
Empty LocalHostName
```
Where can I correct this?

```
QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2008-03-19 18:34:00.234 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
SSDP::PerformSearch - did not write entire buffer.
2008-03-19 18:34:00.304 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
SSDP::PerformSearch - did not write entire buffer.
```

This is strange.  I have had this problem for months.  Oddly after the upgrade I noticed on My XPMCE2005 machine it now recognized my master backend as an UNPN media server.  I got excited on this...It basically just shows a status screen of the machine.  So I am thinking Mythtv .21 upgrades has made me aware of this in the log.

On the slave machine I have in Mythbackend setup the ip of the slave for local machine and the ip of the master.  All are correct and have not changed since install.

```
Could not open settings file /home/mythtv/.mythtv/mysql.txt for writing
```

I checked the file permissions and the info in the file all seems OK.  Group=mythtv and is rwx for all.

Any ideas?

---

### Post by volkswagner on 2008-03-20
Power failure got my off my rear to set static ip's for LAN connected machines.

After setting static ip for the slave and master machines I have joy.

Log after static ip is set, via network manager.

```

2008-03-20 13:45:59.109 Using runtime prefix = /usr, libdir = /usr/lib
2008-03-20 13:45:59.200 Empty LocalHostName.
2008-03-20 13:45:59.231 Using localhost value of Bedroom
2008-03-20 13:45:59.266 Testing network connectivity to 192.168.1.107
2008-03-20 13:45:59.536 New DB connection, total: 1
2008-03-20 13:45:59.694 Connected to database 'mythconverg' at host: 192.168.1.107
2008-03-20 13:45:59.712 Closing DB connection named 'DBManager0'
2008-03-20 13:45:59.807 Connected to database 'mythconverg' at host: 192.168.1.107
2008-03-20 13:45:59.878 New DB connection, total: 2
2008-03-20 13:45:59.911 Connected to database 'mythconverg' at host: 192.168.1.107
2008-03-20 13:45:59.940 Current Schema Version: 1214
Running as a slave backend.
2008-03-20 13:46:00.008 mythbackend: MythBackend started as a slave backend
2008-03-20 13:46:00.051 New DB connection, total: 3
2008-03-20 13:46:00.121 Connected to database 'mythconverg' at host: 192.168.1.107
2008-03-20 13:46:02.164 Main::Registering HttpStatus Extension
2008-03-20 13:46:02.288 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-03-20 13:46:02.302 Enabled verbose msgs:  important general
2008-03-20 13:46:03.310 Connecting to master server: 192.168.1.107:6543
2008-03-20 13:46:03.314 Connected successfully
2008-03-20 13:46:10.049 mythbackend: Running housekeeping thread
```

---

### Post by volkswagner on 2008-03-20
I really need to invest in some UPS units!

:)

---

### Post by newlinux on 2008-03-20
> **volkswagner said:**
> I really need to invest in some UPS units!

:)

They are quite a help. I bit the bullet and did so for all my backends and routers/switches. My uptimes for my 2 primary backends are over 150 days, and that downtime was due to adding new hard drives...

---

