---
title: "frontend will not start on a frontend-only machine"
date: 2008-01-03
forum: Mythbuntu
---

### Post by pasta514 on 2008-01-03
I have two machines.  The backend is all set up and configured (finally!!).  But I'm having trouble with the frontend.

Roughly the history on the frontend machine has been:
Abit AN-M2HD (integrated nvidia 7050 graphics with HDMI on board)
0) connected to VGA monitor::
1) using live CD ; install mythbuntu 64bit on clean hardware
2) under mythcontrol centre; install the proprietary (nvidia) driver v. 100.14.19
3) connect to 720p HDTV via HDMI; it has overscan and could not set the resolution
4) installed ENVY and installed the newest nvidia driver. now v. 100.14.23 ... no difference
5) through the control center installed the gnome desktop and was distracted for a while mucking around with gnome, installing various packages I thought I would find useful. Including enabling lirc through the control center

At this point the frontend machine was working, but the backend was not, so I spent some time working on the backend but was tinkering with the frontend also.  Since the FE machine was hooked to my TV I had to work on the backend machine through my windows PC/Xming.  Regardless, it took a while to get the backend going.

Now, getting back to the frontend...  **somewhere along the way I could no longer start mythfrontend**

6) changed from an HDMI cable to a DSUB VGA cable and was able to configure the HDTV screen for a 1280x768 resolution (no overscan).

I have attempted the following to get this working:
using control center; disabled lirc; never got it working anyway.
using control centre; remove then reinstalled the frontend 'role'
using control center; removed the gnome desktop
using apt-get removed and purged myth-frontend and required dependencies, the rebooted, then using apt-get installed mythtv-frontend
reran envy, but the driver is still 100.14.23 (but nvidia website is showing a new driver as of 20-Dec)

When trying to run it from the menu I get nothing.

the command line output is:

REVISED *Oh dear, I had not waited long enough for the 3 minute time out. perhaps I am having backend problems after all* I originally though the application was hanging. I saw the first 4 lines and assumed that was it. ...

```
papa@ghost:~$ mythfrontend
2008-01-02 23:13:15.756 Using runtime prefix = /usr
2008-01-02 23:13:15.770 Gnome-Screensaver support enabled
2008-01-02 23:13:15.770 DPMS is active.
2008-01-02 23:13:15.790 New DB connection, total: 1
2008-01-02 23:16:24.799 Unable to connect to database!
2008-01-02 23:16:24.799 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.1.160' (110)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-01-02 23:19:33.862 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-01-02 23:22:42.925 Unable to connect to database!
2008-01-02 23:22:42.925 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.1.160' (110)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-01-02 23:25:51.988 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-01-02 23:25:52.040 Database not open while trying to load setting: GuiVidModeResolution
2008-01-02 23:29:01.051 Unable to connect to database!
2008-01-02 23:29:01.051 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.1.160' (110)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-01-02 23:32:10.114 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-01-02 23:32:10.166 Database not open while trying to load setting: GuiVidModeWidth
2008-01-02 23:35:19.177 Unable to connect to database!
2008-01-02 23:35:19.177 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.1.160' (110)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-01-02 23:38:28.244 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-01-02 23:38:28.300 Database not open while trying to load setting: GuiVidModeHeight
2008-01-02 23:41:37.311 Unable to connect to database!
2008-01-02 23:41:37.311 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.1.160' (110)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-01-02 23:44:46.378 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-01-02 23:44:46.434 Database not open while trying to load setting: DisplaySizeResolution
2008-01-02 23:47:55.445 Unable to connect to database!
2008-01-02 23:47:55.445 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:

```
  Please help! Thanks in advance!
1) I'm trying to run myth-frontend
2) I'm going to try to get back to using the HDMI interface rather than the analog.  Do you think this has any bearing on the problem?

---

### Post by volkswagner on 2008-01-03
You need to verify Mysql is running on backend.  Can you ssh into the backend machine from the frontend?  Verify your Mysql password for mythtv is correct.  In control center on backend machine is localhost the location for Mysql?  It should be.

Did you change the password for mythtv user after install?  If you did see here, you will need to tell mysql the new password.  You will need to login to Mysql as root if you did not set a root password, the default is blank.

[http://www.cyberciti.biz/faq/mysql-change-root-password/]("http://www.cyberciti.biz/faq/mysql-change-root-password/")

You should also run
```

sudo dpkg-reconfigure mythtv-database
sudo dpkg-reconfigure mythtv-common
```

Again on the backend mysql location should read localhost, on any machine trying to connect it should be the ip of the backend.

---

### Post by pasta514 on 2008-01-04
> **volkswagner said:**
> You need to verify Mysql is running on backend.  Can you ssh into the backend machine from the frontend?  

Seems my problems were the servers were not automatically starting after rebooting the backend machines.  This backend is not running mythbuntu.
I had to manually start mysql and mythbackend

Now just need to figure out how to make it persistent on booting.:confused:

---

