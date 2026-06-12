---
title: "Mythtv-setup error loop, cant connect to mysql"
date: 2008-03-05
forum: Mythbuntu
---

### Post by Cellwind929 on 2008-03-05
I'm trying to setup mythtv on an ubuntu server 7.10 install. While it isn't mythbuntu, I figured this'd be the the best place for my problem since it's a mythtv problem. Whenever I try and run mythtv-setup, I get hammered with this loop:
```

2008-03-05 01:24:38.668 Using runtime prefix = /usr

2008-03-05 01:24:38.691 Gnome-Screensaver support enabled

2008-03-05 01:24:38.693 DPMS is active.

2008-03-05 01:24:38.746 New DB connection, total: 1

2008-03-05 01:24:41.753 Unable to connect to database!

2008-03-05 01:24:41.753 Driver error was [1/2003]:

QMYSQL3: Unable to connect

Database error was:

Can't connect to MySQL server on '192.168.1.110' (113)



QSqlQuery::exec: database not open

QSqlQuery::exec: database not open

2008-03-05 01:24:44.814 DB Error (KickDatabase):

Query was:

SELECT NULL;

No error type from QSqlError?  Strange...

2008-03-05 01:24:47.873 Unable to connect to database!

2008-03-05 01:24:47.873 Driver error was [1/2003]:

QMYSQL3: Unable to connect

Database error was:

Can't connect to MySQL server on '192.168.1.110' (113)



QSqlQuery::exec: database not open

QSqlQuery::exec: database not open

2008-03-05 01:24:50.933 DB Error (KickDatabase):

Query was:

SELECT NULL;

No error type from QSqlError?  Strange...

2008-03-05 01:24:50.983 Database not open while trying to load setting: GuiVidModeResolution

2008-03-05 01:24:53.993 Unable to connect to database!

2008-03-05 01:24:53.993 Driver error was [1/2003]:

QMYSQL3: Unable to connect

Database error was:

Can't connect to MySQL server on '192.168.1.110' (113)



QSqlQuery::exec: database not open

QSqlQuery::exec: database not open

2008-03-05 01:24:57.053 DB Error (KickDatabase):

Query was:

SELECT NULL;

No error type from QSqlError?  Strange...

2008-03-05 01:24:57.103 Database not open while trying to load setting: GuiVidModeWidth

2008-03-05 01:25:00.113 Unable to connect to database!

2008-03-05 01:25:00.113 Driver error was [1/2003]:

QMYSQL3: Unable to connect

Database error was:

Can't connect to MySQL server on '192.168.1.110' (113)



QSqlQuery::exec: database not open

QSqlQuery::exec: database not open

2008-03-05 01:25:03.173 DB Error (KickDatabase):

Query was:

SELECT NULL;

No error type from QSqlError?  Strange...

2008-03-05 01:25:03.223 Database not open while trying to load setting: GuiVidModeHeight

2008-03-05 01:25:06.233 Unable to connect to database!

2008-03-05 01:25:06.233 Driver error was [1/2003]:

QMYSQL3: Unable to connect

Database error was:

Can't connect to MySQL server on '192.168.1.110' (113)

ETC ETC ETC

```

Apparently mythtv-setup isn't getting into the sql database properly so terminal is just barfing errors at me. eventually it starts the tile blue mythsetup screen, and goes through the setup menus, but I cant change anything.

Thanks to anyone who has solutions.

---

### Post by fastfret79 on 2008-03-08
This is exactly the same error I am getting although I installed Ubunntu Gutsy first and then installed the Mythbunu Control Panel from the Add/Remove section - anyone got any ideas?

---

### Post by fastfret79 on 2008-03-08
I have fixed my error now - I went into the Synaptic Package Manager and removed everything that was Myth and MySQL related, then restarted (not sure if that was necessary) and then re-installed the Mythbuntu Control Panel. 
Hope this helps?!

---

### Post by Cellwind929 on 2008-03-09
The problem is mythsetup isn't hitting the database.

I followed this guide to reset my myth database password.
[https://help.ubuntu.com/community/MythTV/Install/Troubleshooting](https://help.ubuntu.com/community/MythTV/Install/Troubleshooting)

sudo dpkg-reconfigure mythtv-common
will reconfigure the password.

Then I used webmin to log into the mysql server so I don't have to edit config files. The mythtv account didn't have any privialges for the database, so change it so it can hit the database.

Run mythsetup

---

