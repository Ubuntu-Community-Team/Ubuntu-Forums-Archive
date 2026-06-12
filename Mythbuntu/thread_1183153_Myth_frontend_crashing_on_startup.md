---
title: "Myth frontend crashing on startup"
date: 2009-06-09
forum: Mythbuntu
---

### Post by waltm on 2009-06-09
After fighting with system problems for a few weeks I wiped my frontend and re-installed 9.04, nvidia 185 drivers, and mythtv (front end only with with vdapu fixes).  Now I'm not able to start mythtv, it crashes on start up.

Front end log shows the following errors

```

Starting mythfrontend.real..
2009-06-09 19:17:13.837 ERROR: Unable to create schemalock table: Driver error was [2/1005]:
QMYSQL3: Unable to execute query
Database error was:
Can't create table 'schemalock' (errno: 13)

2009-06-09 19:17:13.839 Unexpected DB Schema version.  Waiting to see if DB is being upgraded.
2009-06-09 19:17:14.839 ERROR: Unable to create schemalock table: Driver error was [2/1005]:
QMYSQL3: Unable to execute query
Database error was:
Can't create table 'schemalock' (errno: 13)

2009-06-09 19:17:15.871 ERROR: Unable to create schemalock table: Driver error was [2/1005]:
QMYSQL3: Unable to execute query
Database error was:
Can't create table 'schemalock' (errno: 13)

2009-06-09 19:17:16.872 ERROR: Unable to create schemalock table: Driver error was [2/1005]:
QMYSQL3: Unable to execute query
Database error was:
Can't create table 'schemalock' (errno: 13)

2009-06-09 19:17:17.874 ERROR: Unable to create schemalock table: Driver error was [2/1005]:
QMYSQL3: Unable to execute query
Database error was:
Can't create table 'schemalock' (errno: 13)

2009-06-09 19:17:18.876 ERROR: Unable to create schemalock table: Driver error was [2/1005]:
QMYSQL3: Unable to execute query
Database error was:
Can't create table 'schemalock' (errno: 13)

2009-06-09 19:17:18.877 Timed out waiting.
2009-06-09 19:17:18.877 This version of MythTV requires an updated database schema. Please run mythtv-setup or mythbackend to update your database.
```

Backend log shows 

```
2009-06-09 08:27:47.524 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos; /media/video1:
2009-06-09 08:27:47.527 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-06-09 08:33:15.940 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-09 08:48:15.978 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-09 08:57:54.531 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos; /media/video1:
2009-06-09 08:57:54.535 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-06-09 09:03:16.020 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-09 09:18:16.058 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-09 09:27:57.540 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos; /media/video1:
2009-06-09 09:27:57.543 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-06-09 09:33:16.098 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-09 09:48:16.137 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-09 09:57:59.548 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos; /media/video1:
2009-06-09 09:57:59.551 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-06-09 10:03:16.179 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-09 10:18:16.216 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-09 10:27:59.556 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos; /media/video1:
2009-06-09 10:27:59.561 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-06-09 10:33:16.256 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-09 10:48:16.292 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-09 10:58:03.566 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos; /media/video1:
2009-06-09 10:58:03.571 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-06-09 11:03:16.344 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-09 11:18:16.382 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-09 11:28:07.575 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos; /media/video1:
2009-06-09 11:28:07.579 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-06-09 11:33:16.421 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-09 11:48:16.462 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-09 11:58:13.584 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos; /media/video1:
2009-06-09 11:58:13.587 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-06-09 12:03:16.503 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-09 12:18:16.540 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-09 12:28:17.591 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos; /media/video1:
2009-06-09 12:28:17.596 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-06-09 12:33:16.577 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-09 12:48:16.619 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-09 12:58:17.601 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos; /media/video1:
2009-06-09 12:58:17.609 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-06-09 13:03:16.658 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-09 13:18:16.698 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-09 13:28:23.614 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos; /media/video1:
2009-06-09 13:28:23.619 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-06-09 13:33:16.762 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-09 13:48:16.801 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-09 13:58:27.623 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos; /media/video1:
2009-06-09 13:58:27.628 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-06-09 14:03:16.842 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-09 14:18:16.881 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-09 14:28:29.633 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos; /media/video1:
2009-06-09 14:28:29.640 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-06-09 14:33:16.920 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-09 14:48:16.956 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-09 14:58:33.645 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos; /media/video1:
2009-06-09 14:58:33.651 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-06-09 15:03:16.993 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-09 15:18:17.032 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-09 15:28:36.656 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos; /media/video1:
2009-06-09 15:28:36.659 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-06-09 15:33:17.071 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-09 15:48:17.111 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-09 15:58:43.663 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos; /media/video1:
2009-06-09 15:58:43.667 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-06-09 16:03:17.151 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-09 16:18:17.188 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-09 16:28:49.672 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos; /media/video1:
2009-06-09 16:28:49.675 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-06-09 16:33:17.225 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-09 16:48:17.261 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-09 16:58:55.680 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos; /media/video1:
2009-06-09 16:58:55.685 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-06-09 17:03:17.315 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-09 17:18:17.363 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-09 17:29:00.690 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos; /media/video1:
2009-06-09 17:29:00.695 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-06-09 17:33:17.413 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-09 17:48:17.454 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-09 17:59:01.699 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos; /media/video1:
2009-06-09 17:59:01.703 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-06-09 18:03:17.492 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-09 18:18:17.530 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-09 18:29:07.708 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos; /media/video1:
2009-06-09 18:29:07.712 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-06-09 18:33:17.570 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-09 18:48:17.608 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-09 18:59:09.717 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos; /media/video1:
2009-06-09 18:59:09.719 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-06-09 19:10:44.797 Using runtime prefix = /usr
2009-06-09 19:10:44.912 Empty LocalHostName.
2009-06-09 19:10:44.948 Using localhost value of htpcserver-desktop
2009-06-09 19:10:45.288 New DB connection, total: 1
2009-06-09 19:10:46.215 Connected to database 'mythconverg' at host: localhost
2009-06-09 19:10:46.472 Closing DB connection named 'DBManager0'
2009-06-09 19:10:46.606 Connected to database 'mythconverg' at host: localhost
2009-06-09 19:10:47.051 ERROR: Unable to create schemalock table: Driver error was [2/1005]:
QMYSQL3: Unable to execute query
Database error was:
Can't create table 'schemalock' (errno: 13)

2009-06-09 19:10:47.378 Current Schema Version: 1214
Starting up as the master server.
2009-06-09 19:10:48.037 New DB connection, total: 2
2009-06-09 19:10:48.088 Connected to database 'mythconverg' at host: localhost
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2009-06-09 19:10:48.382 New DB connection, total: 3
2009-06-09 19:10:48.507 Connected to database 'mythconverg' at host: localhost
2009-06-09 19:10:50.296 Main::Registering HttpStatus Extension
2009-06-09 19:10:50.302 mythbackend version: 0.21.20080304-1 www.mythtv.org
2009-06-09 19:10:50.302 Enabled verbose msgs:  important general
2009-06-09 19:10:50.427 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-09 19:10:59.061 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos; /media/video1:
2009-06-09 19:10:59.066 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-06-09 19:12:08.302 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-09 19:12:57.276 Using runtime prefix = /usr
2009-06-09 19:12:57.287 Empty LocalHostName.
2009-06-09 19:12:57.293 Using localhost value of htpcserver-desktop
2009-06-09 19:12:57.306 New DB connection, total: 1
2009-06-09 19:12:57.407 Connected to database 'mythconverg' at host: localhost
2009-06-09 19:12:57.488 Closing DB connection named 'DBManager0'
2009-06-09 19:12:57.627 Connected to database 'mythconverg' at host: localhost
2009-06-09 19:12:57.769 ERROR: Unable to create schemalock table: Driver error was [2/1005]:
QMYSQL3: Unable to execute query
Database error was:
Can't create table 'schemalock' (errno: 13)

2009-06-09 19:12:57.861 Current Schema Version: 1214
Starting up as the master server.
2009-06-09 19:12:58.015 New DB connection, total: 2
2009-06-09 19:12:58.142 Connected to database 'mythconverg' at host: localhost
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
QServerSocket: failed to bind or listen to the socket
2009-06-09 19:12:58.197 MediaServer::HttpServer Create Error
2009-06-09 19:12:58.199 mythbackend version: 0.21.20080304-1 www.mythtv.org
2009-06-09 19:12:58.200 Enabled verbose msgs:  important general
2009-06-09 19:12:58.203 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
QServerSocket: failed to bind or listen to the socket
2009-06-09 19:12:58.272 Failed to bind port 6543. Exiting.
2009-06-09 19:27:08.473 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
```

All frontend logs at [http://mythbuntu.pastebin.com/f22605794](http://mythbuntu.pastebin.com/f22605794)
All backend logs at [http://mythbuntu.pastebin.com/f56539939](http://mythbuntu.pastebin.com/f56539939)


I shutdown and re-started the backend with the same results.  

Does anyone know what might be causing this or what other data I should post to help track this down?


Thanks

---

### Post by crez79 on 2009-06-10
Try to repair/optimize your database. It may not have backedup properly. Is there any chance of rebacking up or is it long gone now? Also you can enable logging of all or most parameters to see if that sheds any light.

---

### Post by waltm on 2009-06-11
Thanks for the tip!  

Trying to auto-repair led to more errors on the backend.  I was haveing issues with it a week or so ago and thought I had it solved.  Turns out I never re-booted and it seemed like it was running fine.  Now that I tried to re-boot it's coming up with a lot of errors, nfs, mysql, gdm not loading, etc.  

I'm currently copying my data files onto a separate partition in preparation for a full re-install of 9.04 and myth.

Thanks for pointing me in the right direction, I didn't even think all the front end issues could be caused by the back end.

---

