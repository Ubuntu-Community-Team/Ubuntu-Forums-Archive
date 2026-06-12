---
title: "mythbackend log errors"
date: 2007-09-23
forum: Multimedia &amp; Video
---

### Post by middlewordie on 2007-09-23
Hi

I've been trying to get mythtv working for some time (two weeks so far) and am having minimal success.

I've just uninstalled and then reinstalled mythtv according to the guide in these forums. However, when I checked the backend log, as recommended, i had two errors:

> nick@sempron2800:~$ more /var/log/mythtv/mythbackend.log
2007-09-23 13:25:20.413 Using runtime prefix = /usr
2007-09-23 13:25:20.571 New DB connection, total: 1
2007-09-23 13:25:20.683 Connected to database 'mythconverg' at host: localhost
2007-09-23 13:25:21.005 Current Schema Version: 1160
Starting up as the master server.
2007-09-23 13:25:23.134 New DB connection, total: 2
2007-09-23 13:25:23.137 Connected to database 'mythconverg' at host: localhost
2007-09-23 13:25:23.175 EITHelper: localtime offset 1:00:00 
2007-09-23 13:25:23.217 New DB connection, total: 3
2007-09-23 13:25:23.220 Connected to database 'mythconverg' at host: localhost
2007-09-23 13:25:25.253 New DB scheduler connection
2007-09-23 13:25:25.257 Connected to database 'mythconverg' at host: localhost
2007-09-23 13:25:25.260 Main::Starting HttpServer
2007-09-23 13:25:25.268 Main::Registering HttpStatus Extension
2007-09-23 13:25:25.312 mythbackend version: 0.20.20060828-3 [www.mythtv.org](www.mythtv.org)
2007-09-23 13:25:25.349 Enabled verbose msgs:  important general
2007-09-23 13:25:25.350 AutoExpire: Found 1 recorders w/max rate of 138 MiB/min
2007-09-23 13:25:25.352 AutoExpire: Required Free Space: 4.0 GB w/freq: 10 min
2007-09-23 13:25:27.278 Reschedule requested for id -1.
2007-09-23 13:25:27.335 Scheduled 0 items in 0.1 = 0.04 match + 0.01 place
2007-09-23 13:25:27.353 Seem to be woken up by USER
2007-09-23 13:26:56.313 EITScanner: Now looking for EIT data on multiplex of cha
nnel 11
2007-09-23 13:27:16.424 match[0]: 0 'Ben Jones' vs. 'The Virgin Radio Album Char
t'
2007-09-23 13:27:18.488 match[0]: 0 'Robin Burke' vs. 'The Late Show with Robin 
Burke'
2007-09-23 13:28:41.211 DB Error (GetOverlappingPrograms 1):
Query was:
SELECT title,          subtitle,      description,        category,       catego
ry_type,        starttime,      endtime,        closecaptioned, subtitled,     s
tereo,      hdtv,        partnumber,     parttotal,        airdate,        origi
nalairdate FROM program WHERE chanid   = 1714 AND       manualid = 0       AND  
     ( ( starttime >= '2007-09-30T02:00:00' AND starttime <  '2007-09-30T06:00:0
0' ) OR         ( endtime   >  '2007-09-30T02:00:00' AND endtime   <= '2007-09-3
0T06:00:00' ) )
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2007-09-23 13:28:41.229 DB Error (InsertDB):
Query was:
REPLACE INTO program (  chanid,         title,          subtitle,        descrip
tion,   category,       category_type,   starttime,      endtime,   closecaption
ed, subtitled,      stereo,          hdtv,   partnumber,     parttotal,   airdat
e,        originalairdate,listingsource ) VALUES ( 1714,        'Smash Hits! Non
-Stop',         '',       'Smash Hits presents non-stop pop music through the ni
ght.',  'Show/game Show',      'tvshow',  '2007-09-30T02:00:00',     '2007-09-30
T06:00:00',  0,            0,     1,         0,  0,    0,  '0000',       NULL,  
 1 )
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2007-09-23 13:31:59.600 EITScanner: Added 173 EIT Events
2007-09-23 13:31:59.661 Reschedule requested for id -1.
2007-09-23 13:31:59.718 Scheduled 0 items in 0.1 = 0.05 match + 0.01 place
2007-09-23 13:32:02.212 EITScanner: Now looking for EIT data on multiplex of cha
nnel 18
2007-09-23 13:37:05.276 EITScanner: Added 101 EIT Events
2007-09-23 13:37:05.285 Reschedule requested for id -1.
2007-09-23 13:37:05.358 Scheduled 0 items in 0.1 = 0.06 match + 0.01 place
2007-09-23 13:37:07.728 EITScanner: Now looking for EIT data on multiplex of cha
nnel 1
2007-09-23 13:42:10.959 EITScanner: Added 382 EIT Events
2007-09-23 13:42:10.966 Reschedule requested for id -1.
2007-09-23 13:42:11.040 Scheduled 0 items in 0.1 = 0.07 match + 0.01 place
2007-09-23 13:42:13.444 EITScanner: Now looking for EIT data on multiplex of cha
nnel 10
2007-09-23 13:43:21.565 EITScanner: Added 26 EIT Events
2007-09-23 13:47:16.701 EITScanner: Added 78 EIT Events
2007-09-23 13:47:16.702 Reschedule requested for id -1.
2007-09-23 13:47:16.785 Scheduled 0 items in 0.1 = 0.08 match + 0.01 place
2007-09-23 13:47:19.042 EITScanner: Now looking for EIT data on multiplex of cha
nnel 15
2007-09-23 13:47:38.127 
EITCache::statistics: Accesses: 50000, Hits: 47099, Table Upgrades 197, New Vers
ions: 594, Entries: 12155 Pruned entries: 0, pruned Hits: 0 Discard channel Hit 
2102 Hit Ratio 0.98402.
2007-09-23 13:48:26.040 EITScanner: Added 37 EIT Events
2007-09-23 14:08:21.895 Using runtime prefix = /usr
2007-09-23 14:08:21.938 New DB connection, total: 1
2007-09-23 14:08:21.944 Connected to database 'mythconverg' at host: localhost
2007-09-23 14:08:21.950 Current Schema Version: 1160
Starting up as the master server.
2007-09-23 14:08:21.961 New DB connection, total: 2
2007-09-23 14:08:22.017 Connected to database 'mythconverg' at host: localhost
2007-09-23 14:08:22.021 EITHelper: localtime offset 1:00:00 
2007-09-23 14:08:22.028 TVRec(2) Error: Start channel from DB is empty, setting 
to '1' instead.
2007-09-23 14:08:22.057 New DB connection, total: 3
2007-09-23 14:08:22.059 Connected to database 'mythconverg' at host: localhost
2007-09-23 14:08:24.113 New DB scheduler connection
2007-09-23 14:08:24.114 Connected to database 'mythconverg' at host: localhost
2007-09-23 14:08:24.117 Main::Starting HttpServer
2007-09-23 14:08:24.157 Main::Registering HttpStatus Extension
2007-09-23 14:08:24.193 mythbackend version: 0.20.20060828-3 [www.mythtv.org](www.mythtv.org)
2007-09-23 14:08:24.197 Enabled verbose msgs:  important general
2007-09-23 14:08:24.198 AutoExpire: Found 1 recorders w/max rate of 138 MiB/min
2007-09-23 14:08:24.205 AutoExpire: Required Free Space: 4.0 GB w/freq: 10 min
2007-09-23 14:08:26.123 Reschedule requested for id -1.
2007-09-23 14:08:26.150 Scheduled 0 items in 0.0 = 0.01 match + 0.02 place
2007-09-23 14:08:26.172 Seem to be woken up by USER
nick@sempron2800:~$ 

Are these serious errors and are they related to the [inability]("http://ubuntuforums.org/showthread.php?t=540904") of the frontend to allow me to watch TV?

Thanks

Nick

---

