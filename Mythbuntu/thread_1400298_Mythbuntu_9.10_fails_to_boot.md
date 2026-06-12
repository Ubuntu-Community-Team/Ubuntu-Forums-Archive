---
title: "Mythbuntu 9.10 fails to boot"
date: 2010-02-06
forum: Mythbuntu
---

### Post by bigwoof on 2010-02-06
Hi there,

I have recently installed mythbuntu 9.10 and am having a little trouble with booting.

Occasionally (every 3 to 4 times the system boots) the system locks up with the following message repeated:

```
init: mythtv-backend main process (XXXX) terminated with status 254
init: mythtv-backend main process, respawning
```

where XXXX is (I assume) the process ID

Any thoughts?

Cheers

Phil

---

### Post by superm1 on 2010-02-07
Check /var/log/mythtv/mythbackend.log to see more information what's going on.

---

### Post by bigwoof on 2010-02-07
Thanks superm1,

I will look at the log and see what I can find.

Cheers

Phil

---

### Post by bigwoof on 2010-02-09
Hi there,

I managed to get the fault to repeat after booting about 10 times this evening.  

Here is the the end of my /var/log/mythtv/mythbackend.log file:

```

................................................................................
2010-02-09 22:19:16.559 UPnPautoconf() - No UPnP backends found
2010-02-09 22:19:16.602 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-02-09 22:19:16.862 Deleting UPnP client...
2010-02-09 22:19:17.390 Failed to init MythContext, exiting.
2010-02-09 22:19:17.516 mythbackend version: branches/release-0-22-fixes [22594] www.mythtv.org
2010-02-09 22:19:17.562 Using runtime prefix = /usr
2010-02-09 22:19:17.604 Using configuration directory = /home/mythtv/.mythtv
2010-02-09 22:19:17.646 Empty LocalHostName.
2010-02-09 22:19:17.688 Using localhost value of philip-desktop
2010-02-09 22:19:17.734 New DB connection, total: 1
2010-02-09 22:19:17.772 Unable to connect to database!
2010-02-09 22:19:17.813 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

................................................................................
2010-02-09 22:19:20.505 UPnPautoconf() - No UPnP backends found
2010-02-09 22:19:20.553 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-02-09 22:19:20.839 Deleting UPnP client...
2010-02-09 22:19:21.329 Failed to init MythContext, exiting.
2010-02-09 22:19:21.469 mythbackend version: branches/release-0-22-fixes [22594] www.mythtv.org
2010-02-09 22:19:21.515 Using runtime prefix = /usr
2010-02-09 22:19:21.565 Using configuration directory = /home/mythtv/.mythtv
2010-02-09 22:19:21.615 Empty LocalHostName.
2010-02-09 22:19:21.665 Using localhost value of philip-desktop
2010-02-09 22:19:21.720 New DB connection, total: 1
2010-02-09 22:19:21.765 Unable to connect to database!
2010-02-09 22:19:21.815 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

2010-02-09 22:20:47.887 mythbackend version: branches/release-0-22-fixes [22594] www.mythtv.org
2010-02-09 22:20:47.951 Using runtime prefix = /usr
2010-02-09 22:20:48.009 Using configuration directory = /home/mythtv/.mythtv
2010-02-09 22:20:48.104 Empty LocalHostName.
2010-02-09 22:20:48.143 Using localhost value of philip-desktop
2010-02-09 22:20:48.276 New DB connection, total: 1
2010-02-09 22:20:48.373 Connected to database 'mythconverg' at host: localhost
2010-02-09 22:20:48.410 Closing DB connection named 'DBManager0'
2010-02-09 22:20:48.461 Connected to database 'mythconverg' at host: localhost
2010-02-09 22:20:48.616 Current MythTV Schema Version (DBSchemaVer): 1244
2010-02-09 22:20:48.654 MythBackend: Starting up as the master server.
2010-02-09 22:20:48.778 New DB connection, total: 2
2010-02-09 22:20:48.869 Connected to database 'mythconverg' at host: localhost
2010-02-09 22:20:51.448 New DB connection, total: 3
2010-02-09 22:20:51.566 Connected to database 'mythconverg' at host: localhost
2010-02-09 22:21:00.518 New DB scheduler connection
2010-02-09 22:21:00.669 Connected to database 'mythconverg' at host: localhost
2010-02-09 22:21:00.814 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2010-02-09 22:21:00.969 Main::Registering HttpStatus Extension
2010-02-09 22:21:01.062 Enabled verbose msgs:  important general
2010-02-09 22:21:01.189 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-09 22:21:03.839 Reschedule requested for id -1.
2010-02-09 22:21:04.142 Scheduled 0 items in 0.3 = 0.16 match + 0.15 place
2010-02-09 22:21:04.397 Seem to be woken up by USER
2010-02-09 22:21:05.563 MainServer::ANN Monitor
2010-02-09 22:21:05.604 adding: philip-desktop as a client (events: 0)
2010-02-09 22:21:05.654 MainServer::ANN Monitor
2010-02-09 22:21:05.712 adding: philip-desktop as a client (events: 1)
2010-02-09 22:22:20.777 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
```

The first 2 sections are repeated multiple times (I assume that this is when it is attempting to respawn the mythtv-backend process).  I think that the last section is from when the machine booted successfully.

It looks like there is some trouble connecting to the MySQL database, but I have no idea where to go from here.  

Any thoughts?

Cheers

Phil

---

### Post by ian dobson on 2010-02-09
Hi,

It looks as if mythbackend is starting before the mysql database is finished loading.

Mythbuntu 9.10 uses upstart to start quite afew jobs rather than the "old" init.d method, and it could be that upstart is trying to start the backend process too soon. 

I still haven't got my brain around upstart, so I'm not sure the best way to delay the startup of mythbackend until mysql is running.

Maybe superm1 has an idea.

Regards
Ian Dobson

---

### Post by superm1 on 2010-02-09
The first two "failed" to start cases are harmless if it comes up on the third.  Ian is right though that it's mysql and myth racing.

---

### Post by bigwoof on 2010-02-09
Hi There,

Thanks for pointing me in the right direction.  I found this that will hopefully help:

[https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/470672](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/470672)

I will give the suggestions a shot and see if they work.

Cheers

Phil

PS: Mario I heard you on the mythtvcast. Your efforts are greatly appreciated :)

---

### Post by bigwoof on 2010-02-12
Hi There,

I have hopefully fixed the problem.

I found the solution in the link in my previous post.

I added the following to /etc/init/mythtv-backend.conf

```
pre-start script
   /etc/init.d/mysql start
end script
```

As far as I can tell this makes the upstart command that starts the mythtv-backend also start mysql. The original mysql startup command still runs but doesn't do anything if the DB has already been started.

Cheers

Phil

---

