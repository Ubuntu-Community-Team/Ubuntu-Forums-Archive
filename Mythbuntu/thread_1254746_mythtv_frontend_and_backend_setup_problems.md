---
title: "mythtv frontend and backend setup problems?"
date: 2009-08-31
forum: Mythbuntu
---

### Post by abrylow on 2009-08-31
Ok so I'm totally new to Linux, and I just installed mythbuntu a few days ago.  Ever since then I've been trying to get it to work, but whenever I open the frontend, it wont open until a random time later on, and then I get an error saying "No uPnP backend found" when it does open.  And when I try to open the backend setup, i get an error saying I need to close open instances of the backend and it asks if I would like to do that.  When I click ok, a  backend setup terminal type window opens up.  When I close that, it asks if i would like to open "mythfilldatabase" and another terminal window pops up.  

I know, I know, its probably something very easy and I should know the answer, but I've been doing nothing but reading how-to's and installation manuals on mythbuntu and I cannot seem to figure this out.  ANY help at all would be greatly appreciated. Thanks

---

### Post by mitchell2345 on 2009-08-31
> **abrylow said:**
> Ok so I'm totally new to Linux, and I just installed mythbuntu a few days ago.  Ever since then I've been trying to get it to work, but whenever I open the frontend, it wont open until a random time later on, and then I get an error saying "No uPnP backend found" when it does open.  And when I try to open the backend setup, i get an error saying I need to close open instances of the backend and it asks if I would like to do that.  When I click ok, a  backend setup terminal type window opens up.  When I close that, it asks if i would like to open "mythfilldatabase" and another terminal window pops up.  

I know, I know, its probably something very easy and I should know the answer, but I've been doing nothing but reading how-to's and installation manuals on mythbuntu and I cannot seem to figure this out.  ANY help at all would be greatly appreciated. Thanks

No backends are found because you must configure it first in mythtv-setup.

looks like mythtv-setup is failing to load.  If you open up terminal and type mythtv-setup do you see any errors in the output.  Please post the log file.

Mitchell

---

### Post by williammanda on 2009-09-06
Did you follow through the mythbuntu control center? This process will walk you through the complete setup and should have you working within an hour.
Thanks

---

### Post by trevs.bronco on 2009-09-07
I'm having similar problems on my remote backend. I haven't made any changes that I'm aware of except for regular updates. the backend used to connect without issue but as time goes on it connects less and less, it has been a few days now since I have been able to get it to connect. the most I have been able to get is the background of the theme. all IP addresses are correct in both the frontend setup and the backend and the password for MYSQL is correct. I am able to ping the backend and my NFS shares work. any one have any idea of what might be causing this?

Trev

---

### Post by williammanda on 2009-09-07
Post your logs for the frontend & backend. Goto /var/log/mythtv to get the logs.
Thanks

---

### Post by trevs.bronco on 2009-09-07
Here is a chunk of the frontend log from when I was unable to connect. even now that I am connected it still takes a few minutes for requests to be filled when going through the menus. 

```
2009-09-05 22:18:27.724 nice /usr/share/mythtv/mythweather/scripts/us_nws/maps.pl -u ENG -d /home/trev/.mythtv/MythWeather/Map-Download http://image.weather.com/images/sat/canadasat_720x486.jpg has exited
2009-09-05 22:23:25.692 Starting update of ENVCAN
2009-09-05 22:23:26.150 nice /usr/share/mythtv/mythweather/scripts/ca_envcan/envcan.pl -u SI -d /home/trev/.mythtv/MythWeather/ENVCAN bc-74 has exited
2009-09-05 22:24:57.810 XMLParse::LoadTheme using /usr/share/mythtv/themes/glass-wide/ui.xml
Image needs a name
Starting mythfrontend.real..
2009-09-05 23:06:40.205 New DB connection, total: 2
2009-09-05 23:07:13.131 Connected to database 'mythconverg' at host: 192.168.2.2
2009-09-05 23:08:18.983 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-09-05 23:08:18.983 Enabled verbose msgs:  important general
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
2009-09-05 23:26:58.600 New DB connection, total: 2
2009-09-05 23:27:31.543 Connected to database 'mythconverg' at host: 192.168.2.2
2009-09-05 23:28:05.484 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-09-05 23:28:05.485 Enabled verbose msgs:  important general
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
2009-09-06 00:01:35.481 No theme dir: /home/trev/.mythtv/themes/glass-wide
2009-09-06 00:02:06.410 Primary screen 0.
2009-09-06 00:02:07.406 Using screen 0, 1280x720 at 0,0
2009-09-06 00:02:07.408 No theme dir: /home/trev/.mythtv/themes/glass-wide
2009-09-06 00:02:07.409 Switching to wide mode (glass-wide)
Starting mythfrontend.real..
2009-09-06 17:52:51.541 New DB connection, total: 2
2009-09-06 17:53:05.809 Connected to database 'mythconverg' at host: 192.168.2.2
2009-09-06 17:53:53.193 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-09-06 17:53:53.193 Enabled verbose msgs:  important general
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
2009-09-06 18:59:04.147 DB Error (SimpleDBStorage::load()):
Query was:
SELECT data FROM settings WHERE value = 'MythFillDatabaseArgs'
Driver error was [2/2013]:
QMYSQL3: Unable to execute query
Database error was:
Lost connection to MySQL server during query

QSqlQuery::exec: database not open
2009-09-06 19:02:13.197 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
QSqlQuery::exec: database not open
2009-09-06 19:02:13.247 DB Error (SimpleDBStorage::load()):
Query was:
SELECT data FROM settings WHERE value = :WHEREVALUE
No error type from QSqlError?  Strange...
2009-09-06 19:02:25.251 Unable to connect to database!
2009-09-06 19:02:25.251 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.2.2' (113)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-09-06 19:02:28.305 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
QSqlQuery::exec: database not open
2009-09-06 19:02:28.355 DB Error (SimpleDBStorage::load()):
Query was:
SELECT data FROM settings WHERE value = :WHEREVALUE
No error type from QSqlError?  Strange...
2009-09-06 19:04:04.359 Unable to connect to database!
2009-09-06 19:04:04.359 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.2.2' (113)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-09-06 19:04:07.413 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
QSqlQuery::exec: database not open
2009-09-06 19:04:07.463 DB Error (SimpleDBStorage::load()):
Query was:
SELECT data FROM settings WHERE value = :WHEREVALUE
No error type from QSqlError?  Strange...
2009-09-06 19:04:10.467 Unable to connect to database!
2009-09-06 19:04:10.467 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.2.2' (113)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-09-06 19:04:13.521 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
QSqlQuery::exec: database not open
2009-09-06 19:04:13.571 DB Error (SimpleDBStorage::load()):
Query was:
SELECT data FROM settings WHERE value = :WHEREVALUE
No error type from QSqlError?  Strange...
2009-09-06 19:04:16.575 Unable to connect to database!
2009-09-06 19:04:16.575 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.2.2' (113)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-09-06 19:04:19.629 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
QSqlQuery::exec: database not open
2009-09-06 19:04:19.679 DB Error (SimpleDBStorage::load()):
Query was:
SELECT data FROM settings WHERE value = :WHEREVALUE
No error type from QSqlError?  Strange...
2009-09-06 19:04:22.683 Unable to connect to database!
2009-09-06 19:04:22.683 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.2.2' (113)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-09-06 19:04:25.737 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
QSqlQuery::exec: database not open
2009-09-06 19:04:25.787 DB Error (SimpleDBStorage::save() query):
Query was:
SELECT * FROM settings WHERE value = :WHEREVALUE;
No error type from QSqlError?  Strange...
2009-09-06 19:04:28.791 Unable to connect to database!
2009-09-06 19:04:28.791 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.2.2' (113)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-09-06 19:04:31.845 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
QSqlQuery::exec: database not open
2009-09-06 19:04:31.895 DB Error (SimpleDBStorage::save() query):
Query was:
SELECT * FROM settings WHERE value = :WHEREVALUE;
No error type from QSqlError?  Strange...
2009-09-06 19:04:34.899 Unable to connect to database!
2009-09-06 19:04:34.899 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.2.2' (113)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-09-06 19:04:37.953 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
QSqlQuery::exec: database not open
2009-09-06 19:04:38.003 DB Error (SimpleDBStorage::save() query):
Query was:
SELECT * FROM settings WHERE value = :WHEREVALUE;
No error type from QSqlError?  Strange...
2009-09-06 19:04:41.007 Unable to connect to database!
2009-09-06 19:04:41.007 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.2.2' (113)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-09-06 19:04:44.061 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
QSqlQuery::exec: database not open
2009-09-06 19:04:44.111 DB Error (SimpleDBStorage::save() query):
Query was:
SELECT * FROM settings WHERE value = :WHEREVALUE;
No error type from QSqlError?  Strange...
2009-09-06 19:04:47.115 Unable to connect to database!
2009-09-06 19:04:47.115 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.2.2' (113)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-09-06 19:04:50.169 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
QSqlQuery::exec: database not open
2009-09-06 19:04:50.219 DB Error (SimpleDBStorage::save() query):
Query was:
SELECT * FROM settings WHERE value = :WHEREVALUE;
No error type from QSqlError?  Strange...
2009-09-06 19:04:53.223 Unable to connect to database!
2009-09-06 19:04:53.223 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.2.2' (113)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-09-06 19:04:56.277 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
QSqlQuery::exec: database not open
2009-09-06 19:04:56.327 DB Error (SimpleDBStorage::save() query):
Query was:
SELECT * FROM settings WHERE value = :WHEREVALUE;
No error type from QSqlError?  Strange...
2009-09-06 19:04:59.331 Unable to connect to database!
2009-09-06 19:04:59.331 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.2.2' (113)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-09-06 19:05:02.385 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
QSqlQuery::exec: database not open
2009-09-06 19:05:02.435 DB Error (SimpleDBStorage::load()):
Query was:
SELECT data FROM settings WHERE value = :WHEREVALUE
No error type from QSqlError?  Strange...
2009-09-06 19:05:31.357 Unable to connect to database!
2009-09-06 19:05:31.357 Driver error was [1/2013]:
QMYSQL3: Unable to connect
Database error was:
Lost connection to MySQL server at 'reading authorization packet', system error: 0

QSqlQuery::exec: database not open
2009-09-06 19:09:04.821 No theme dir: /home/trev/.mythtv/themes/glass-wide
2009-09-06 19:09:06.822 Primary screen 0.
2009-09-06 19:09:37.759 Using screen 0, 1280x720 at 0,0
2009-09-06 19:09:39.746 No theme dir: /home/trev/.mythtv/themes/glass-wide
2009-09-06 19:09:39.747 Switching to wide mode (glass-wide)
2009-09-06 19:13:28.265 Using the Qt painter
2009-09-06 19:13:28.266 JoystickMenuClient Error: Joystick disabled - Failed to read /home/trev/.mythtv/joystickmenurc
mythtv: could not connect to socket
mythtv: No such file or directory
2009-09-06 19:13:28.267 lirc_init failed for mythtv, see preceding messages
2009-09-06 19:20:36.302 Loading from: /usr/share/mythtv/themes/glass-wide/base.xml
2009-09-06 19:20:36.422 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-09-06 20:03:57.548 Registering Internal as a media playback plugin.
2009-09-06 20:33:04.681 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-09-06 20:33:37.677 Failed to run 'cdrecord --scanbus'
2009-09-06 20:33:37.688 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-09-06 20:33:37.700 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-09-06 21:13:41.107 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-09-06 21:51:23.603 DB Error (SimpleDBStorage::load()):
Query was:
SELECT data FROM settings WHERE value = 'VideoGalleryColsPerPage' AND hostname = 'luv-shack'
Driver error was [2/2013]:
QMYSQL3: Unable to execute query
Database error was:
Lost connection to MySQL server during query

QSqlQuery::exec: database not open
2009-09-06 21:54:32.653 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
QSqlQuery::exec: database not open
2009-09-06 21:54:32.703 DB Error (SimpleDBStorage::load()):
Query was:
SELECT data FROM settings WHERE value = :WHEREVALUE AND hostname = :WHEREHOSTNAME
No error type from QSqlError?  Strange...
2009-09-06 21:56:08.707 Unable to connect to database!
2009-09-06 21:56:08.707 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.2.2' (113)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-09-06 21:56:11.761 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
QSqlQuery::exec: database not open
2009-09-06 21:56:11.811 DB Error (SimpleDBStorage::load()):
Query was:
SELECT data FROM settings WHERE value = :WHEREVALUE AND hostname = :WHEREHOSTNAME
No error type from QSqlError?  Strange...
2009-09-06 21:56:14.815 Unable to connect to database!
2009-09-06 21:56:14.815 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.2.2' (113)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-09-06 21:56:17.869 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
QSqlQuery::exec: database not open
2009-09-06 21:56:17.919 DB Error (SimpleDBStorage::load()):
Query was:
SELECT data FROM settings WHERE value = :WHEREVALUE AND hostname = :WHEREHOSTNAME
No error type from QSqlError?  Strange...
2009-09-06 21:56:20.923 Unable to connect to database!
2009-09-06 21:56:20.923 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.2.2' (113)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-09-06 21:56:23.977 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
QSqlQuery::exec: database not open
2009-09-06 21:56:24.027 DB Error (SimpleDBStorage::load()):
Query was:
SELECT data FROM settings WHERE value = :WHEREVALUE AND hostname = :WHEREHOSTNAME
No error type from QSqlError?  Strange...
2009-09-06 21:57:12.031 Unable to connect to database!
2009-09-06 21:57:12.031 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.2.2' (113)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-09-06 21:57:15.085 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
QSqlQuery::exec: database not open
2009-09-06 21:57:15.136 DB Error (SimpleDBStorage::load()):
Query was:
SELECT data FROM settings WHERE value = :WHEREVALUE AND hostname = :WHEREHOSTNAME
No error type from QSqlError?  Strange...
2009-09-06 21:57:18.139 Unable to connect to database!
2009-09-06 21:57:18.139 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.2.2' (113)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-09-06 21:57:21.193 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
QSqlQuery::exec: database not open
2009-09-06 21:57:21.243 DB Error (SimpleDBStorage::load()):
Query was:
SELECT data FROM settings WHERE value = :WHEREVALUE AND hostname = :WHEREHOSTNAME
No error type from QSqlError?  Strange...
2009-09-06 21:57:24.247 Unable to connect to database!
2009-09-06 21:57:24.247 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.2.2' (113)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-09-06 21:57:27.301 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
QSqlQuery::exec: database not open
2009-09-06 21:57:27.351 DB Error (SimpleDBStorage::load()):
Query was:
SELECT data FROM settings WHERE value = :WHEREVALUE AND hostname = :WHEREHOSTNAME
No error type from QSqlError?  Strange...
2009-09-06 21:57:30.355 Unable to connect to database!
2009-09-06 21:57:30.355 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.2.2' (113)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-09-06 22:00:39.405 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
QSqlQuery::exec: database not open
2009-09-06 22:00:39.455 DB Error (SimpleDBStorage::load()):
Query was:
SELECT data FROM settings WHERE value = :WHEREVALUE AND hostname = :WHEREHOSTNAME
No error type from QSqlError?  Strange...
2009-09-06 22:00:42.459 Unable to connect to database!
2009-09-06 22:00:42.459 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.2.2' (113)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-09-06 22:00:45.513 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
QSqlQuery::exec: database not open
2009-09-06 22:00:45.563 DB Error (SimpleDBStorage::load()):
Query was:
SELECT data FROM settings WHERE value = :WHEREVALUE AND hostname = :WHEREHOSTNAME
No error type from QSqlError?  Strange...
2009-09-06 22:00:48.567 Unable to connect to database!
2009-09-06 22:00:48.567 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.2.2' (113)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-09-06 22:03:57.617 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
QSqlQuery::exec: database not open
2009-09-06 22:03:57.667 DB Error (SimpleDBStorage::load()):
Query was:
SELECT data FROM settings WHERE value = :WHEREVALUE AND hostname = :WHEREHOSTNAME
No error type from QSqlError?  Strange...
2009-09-06 22:04:00.671 Unable to connect to database!
2009-09-06 22:04:00.671 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.2.2' (113)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-09-06 22:04:03.725 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
QSqlQuery::exec: database not open
2009-09-06 22:04:03.775 DB Error (SimpleDBStorage::load()):
Query was:
SELECT data FROM settings WHERE value = :WHEREVALUE AND hostname = :WHEREHOSTNAME
No error type from QSqlError?  Strange...
2009-09-06 22:04:06.779 Unable to connect to database!
2009-09-06 22:04:06.779 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.2.2' (113)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-09-06 22:04:09.833 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
QSqlQuery::exec: database not open
2009-09-06 22:04:09.883 DB Error (SimpleDBStorage::load()):
Query was:
SELECT data FROM settings WHERE value = :WHEREVALUE AND hostname = :WHEREHOSTNAME
No error type from QSqlError?  Strange...
2009-09-06 22:04:12.887 Unable to connect to database!
2009-09-06 22:04:12.887 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.2.2' (113)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-09-06 22:04:15.941 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
QSqlQuery::exec: database not open
2009-09-06 22:04:15.991 DB Error (SimpleDBStorage::save() query):
Query was:
SELECT * FROM settings WHERE value = :WHEREVALUE AND hostname = :WHEREHOSTNAME;
No error type from QSqlError?  Strange...
2009-09-06 22:04:18.995 Unable to connect to database!
2009-09-06 22:04:18.995 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.2.2' (113)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-09-06 22:04:22.049 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
QSqlQuery::exec: database not open
2009-09-06 22:04:22.099 DB Error (SimpleDBStorage::save() query):
Query was:
SELECT * FROM settings WHERE value = :WHEREVALUE AND hostname = :WHEREHOSTNAME;
No error type from QSqlError?  Strange...
2009-09-06 22:07:31.099 Unable to connect to database!
2009-09-06 22:07:31.099 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.2.2' (110)

QSqlQuery::exec: database not open
2009-09-06 22:17:20.708 Starting update of BBC-Current-XML
2009-09-06 22:17:20.718 Starting update of BBC-3day-XML
2009-09-06 22:17:20.726 Starting update of ENVCAN
2009-09-06 22:17:20.735 Starting update of Map-Download
2009-09-06 22:17:20.744 Starting update of ENVCAN-Animated-Map
2009-09-06 22:18:24.563 No theme dir: /home/trev/.mythtv/themes/glass-wide
2009-09-06 22:21:38.606 XMLParse::LoadTheme using /usr/share/mythtv/themes/glass-wide/ui.xml
Image needs a name
2009-09-06 22:23:21.960 Connecting to backend server: 192.168.2.2:6543 (try 1 of 5)
2009-09-06 22:23:21.962 Using protocol version 40
2009-09-06 22:24:28.852 XMLParse::LoadTheme using /usr/share/mythtv/themes/glass-wide/ui.xml
Image needs a name
2009-09-06 22:25:32.683 No theme dir: /home/trev/.mythtv/themes/glass-wide
2009-09-06 22:25:33.644 nice /usr/share/mythtv/mythweather/scripts/uk_bbc/bbccurrentxml.pl -u SI -d /home/trev/.mythtv/MythWeather/BBC-Current-XML W6671 has exited
```

---

### Post by trevs.bronco on 2009-09-09
I think some of my problems might be related to the high latency i am experiencing, pinging my router produces results in the 4000ms-5000ms+. any ideas on what might cause that kind of result. by comparison my backend machine is around 1000ms with every 5th ping or so down around 50ms. a windows machine connecting with wireless g is getting around 2000ms. this is on a belkin F5d8233-[I]4 router. should i just junk this and get something better?

Trev
[/I]

---

