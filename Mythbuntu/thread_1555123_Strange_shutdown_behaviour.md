---
title: "Strange shutdown behaviour"
date: 2010-08-17
forum: Mythbuntu
---

### Post by myth01 on 2010-08-17
Hi all

My box had been running fine for a while, having followed the ACPI_Wakeup instructions it was powering on and off just as it should, but recently this has been appearing in the backend log when it tries to shutdown:

```
2010-08-17 07:38:31.328 I'm idle now... shutdown will occur in 60 seconds.
2010-08-17 07:39:30.355 Running the command to set the next scheduled wakeup time :-
						mythshutdown --setwakeup 2010-08-17T22:25:00
2010-08-17 07:39:30.474 Running the command to shutdown this computer :-
						mythshutdown --shutdown
2010-08-17 07:39:46.681 mythbackend version: branches/release-0-23-fixes [25423] www.mythtv.org
2010-08-17 07:39:46.971 Using runtime prefix = /usr
2010-08-17 07:39:47.045 Using configuration directory = /home/mythtv/.mythtv
2010-08-17 07:39:47.062 Empty LocalHostName.
2010-08-17 07:39:47.077 Using localhost value of server
2010-08-17 07:39:47.109 New DB connection, total: 1
2010-08-17 07:39:47.110 Unable to connect to database!
2010-08-17 07:39:47.110 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

................................................................................
2010-08-17 07:39:49.817 UPnPautoconf() - No UPnP backends found
2010-08-17 07:39:49.819 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-08-17 07:39:49.822 Deleting UPnP client...
2010-08-17 07:39:50.408 Failed to init MythContext, exiting.
2010-08-17 07:39:50.483 mythbackend version: branches/release-0-23-fixes [25423] www.mythtv.org
2010-08-17 07:39:50.484 Using runtime prefix = /usr
2010-08-17 07:39:50.485 Using configuration directory = /home/mythtv/.mythtv
2010-08-17 07:39:50.485 Empty LocalHostName.
2010-08-17 07:39:50.486 Using localhost value of server
2010-08-17 07:39:50.493 New DB connection, total: 1
2010-08-17 07:39:50.494 Unable to connect to database!
2010-08-17 07:39:50.494 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

................................................................................
2010-08-17 07:39:53.052 UPnPautoconf() - No UPnP backends found
2010-08-17 07:39:53.054 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-08-17 07:39:53.056 Deleting UPnP client...
2010-08-17 07:39:53.664 Failed to init MythContext, exiting.
2010-08-17 07:39:53.739 mythbackend version: branches/release-0-23-fixes [25423] www.mythtv.org
2010-08-17 07:39:53.740 Using runtime prefix = /usr
2010-08-17 07:39:53.741 Using configuration directory = /home/mythtv/.mythtv
2010-08-17 07:39:53.741 Empty LocalHostName.
2010-08-17 07:39:53.742 Using localhost value of server
2010-08-17 07:39:53.749 New DB connection, total: 1
2010-08-17 07:39:53.751 Unable to connect to database!
2010-08-17 07:39:53.751 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

................................................................................
2010-08-17 07:39:56.309 UPnPautoconf() - No UPnP backends found
2010-08-17 07:39:56.311 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-08-17 07:39:56.313 Deleting UPnP client...
2010-08-17 07:39:56.730 mythbackend version: branches/release-0-23-fixes [25423] www.mythtv.org
2010-08-17 07:39:56.733 Using runtime prefix = /usr
2010-08-17 07:39:56.745 Using configuration directory = /home/mythtv/.mythtv
2010-08-17 07:39:56.746 Empty LocalHostName.
2010-08-17 07:39:56.747 Using localhost value of server
2010-08-17 07:39:56.756 New DB connection, total: 1
2010-08-17 07:39:56.757 Unable to connect to database!
2010-08-17 07:39:56.757 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

................................................................................
2010-08-17 07:39:59.342 UPnPautoconf() - No UPnP backends found
2010-08-17 07:39:59.664 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-08-17 07:39:59.666 Deleting UPnP client...
2010-08-17 07:39:59.667 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-08-17 20:56:42.201 mythbackend version: branches/release-0-23-fixes [25423] www.mythtv.org
2010-08-17 20:56:42.273 Using runtime prefix = /usr
```

It does shutdown but it looks to me like the backend is restarting (at 07:39:46.681) and having trouble with a database connection.

Any ideas?

Cheers
Matt

---

