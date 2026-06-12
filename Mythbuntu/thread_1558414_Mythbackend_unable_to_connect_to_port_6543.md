---
title: "Mythbackend unable to connect to port 6543"
date: 2010-08-22
forum: Mythbuntu
---

### Post by SquareRootofBlue on 2010-08-22
I've just installed MythTV on Ubuntu 10.04 from repositories but the backend keeps crashing trying to connect to port 6543 even though it is listed as having 2 local connections (which could only be from Myth) in netstat.
> 
myth@myth-desktop:~$ mythbackend
2010-08-22 12:44:14.909 mythbackend version: branches/release-0-23-fixes [24158] [www.mythtv.org](www.mythtv.org)
2010-08-22 12:44:14.909 Using runtime prefix = /usr
2010-08-22 12:44:14.909 Using configuration directory = /home/fmyth/.mythtv
2010-08-22 12:44:14.910 Empty LocalHostName.
2010-08-22 12:44:14.910 Using localhost value of fmyth-desktop
2010-08-22 12:44:14.914 New DB connection, total: 1
2010-08-22 12:44:14.917 Connected to database 'mythconverg' at host: localhost
2010-08-22 12:44:14.917 Closing DB connection named 'DBManager0'
2010-08-22 12:44:14.917 Connected to database 'mythconverg' at host: localhost
2010-08-22 12:44:14.919 Current MythTV Schema Version (DBSchemaVer): 1254
2010-08-22 12:44:14.920 MythBackend: Starting up as the master server.
2010-08-22 12:44:14.922 New DB connection, total: 2
2010-08-22 12:44:14.922 Connected to database 'mythconverg' at host: localhost
2010-08-22 12:44:14.946 New DB connection, total: 3
2010-08-22 12:44:14.947 Connected to database 'mythconverg' at host: localhost
2010-08-22 12:44:15.815 New DB scheduler connection
2010-08-22 12:44:15.816 Connected to database 'mythconverg' at host: localhost
2010-08-22 12:44:15.824 MediaServer::HttpServer Create Error
2010-08-22 12:44:15.825 Enabled verbose msgs:  important general
2010-08-22 12:44:15.826 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-08-22 12:44:15.828 Failed to bind port 6543. Exiting.
2010-08-22 12:44:15.828 Backend exiting, MainServer initialization error.
myth@myth-desktop:~$ netstat | grep 6543
tcp        0      0 localhost:47086         localhost:6543          ESTABLISHED
tcp        0      0 localhost:6543          localhost:47086         ESTABLISHED
myth@myth-desktop:~$ 


Does anyone know what's causing this?

---

### Post by ian dobson on 2010-08-22
Hi,

The error means that something else is already listening in port 6543, which usually means mythbackend is already running.

The backend process usually runs as a deamon in the background, and is started on bootup.

If you want to see if te backend is already running, just go to the terminal and type:-

sudo ps -A | grep myth


Regards
Ian Dobson

---

