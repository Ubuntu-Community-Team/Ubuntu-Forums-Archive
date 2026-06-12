---
title: "MythTV- can't run mythtv-setup after installing"
date: 2007-05-09
forum: Multimedia &amp; Video
---

### Post by fldavem on 2007-05-09
I've just installed mythtv on my ubuntu (feisty) box and having trouble getting the setup going. When I run the mythtv-set (from a terminal or from the menu System>Administration>MythTv Backend Setup, it immediately tells me it has to stop the current setup (which I don't think is even running) then goes straight into asking me if it should run mythfilldatabase, which also doesn't do anything. Here is the output when I try and run mythtv-setup:

[INDENT]dave@p4ubuntu:~$ mythtv-setup
Stopping MythTV server: mythbackend No /usr/bin/mythbackend found running; none killed.
.
2007-05-06 22:03:35.926 Using runtime prefix = /usr
2007-05-06 22:03:35.941 Gnome-Screensaver support enabled
2007-05-06 22:03:35.941 DPMS is active.
2007-05-06 22:03:35.970 New DB connection, total: 1
2007-05-06 22:03:35.975 Connected to database 'mythconverg' at host: localhost
2007-05-06 22:03:35.977 Total desktop dim: 900x1440, with 2 screen[s].
2007-05-06 22:03:35.980 Using screen 0, 900x1440 at 0,0
2007-05-06 22:03:36.002 Current Schema Version: 1160
Segmentation fault (core dumped)
Restarting MythTV server: mythbackend No /usr/bin/mythbackend found running; none killed.
.
.
dave@p4ubuntu:~$[/INDENT]

Also, here is the listing in the mythbackend.log file:

[INDENT]2007-05-06 22:03:47.540 Using runtime prefix = /usr
2007-05-06 22:03:47.610 New DB connection, total: 1
2007-05-06 22:03:47.617 Connected to database 'mythconverg' at host: localhost
2007-05-06 22:03:47.622 Current Schema Version: 1160
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.
dave@p4ubuntu:~$[/INDENT]

I've just done an uninstall and then went and followed the directions for installing the frontend/backend/desktop and here's more information:

I typed mythtv-setup > a file and got this in the file:
[INDENT]2007-05-09 21:29:50.723 Using runtime prefix = /usr
2007-05-09 21:29:50.735 Gnome-Screensaver support enabled
2007-05-09 21:29:50.735 DPMS is active.
2007-05-09 21:29:50.750 New DB connection, total: 1
2007-05-09 21:29:50.755 Connected to database 'mythconverg' at host: localhost
2007-05-09 21:29:50.757 Total desktop dim: 900x1440, with 2 screen[s].
2007-05-09 21:29:50.759 MSqlQuery: SELECT data FROM settings WHERE value = 'RunFrontendInWindow' AND hostname = 'p4ubuntu' ;
2007-05-09 21:29:50.760 MSqlQuery: SELECT data FROM settings WHERE value = 'RunFrontendInWindow' AND hostname IS NULL;
2007-05-09 21:29:50.760 Using screen 1, 900x1440 at 0,0
2007-05-09 21:29:50.761 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiOffsetX' AND hostname = 'p4ubuntu' ;
2007-05-09 21:29:50.761 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiOffsetX' AND hostname IS NULL;
2007-05-09 21:29:50.762 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiOffsetY' AND hostname = 'p4ubuntu' ;
2007-05-09 21:29:50.762 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiOffsetY' AND hostname IS NULL;
2007-05-09 21:29:50.763 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiResolution' AND hostname = 'p4ubuntu' ;
2007-05-09 21:29:50.763 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiResolution' AND hostname IS NULL;
2007-05-09 21:29:50.763 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiWidth' AND hostname = 'p4ubuntu' ;
2007-05-09 21:29:50.764 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiWidth' AND hostname IS NULL;
2007-05-09 21:29:50.764 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiHeight' AND hostname = 'p4ubuntu' ;
2007-05-09 21:29:50.765 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiHeight' AND hostname IS NULL;
2007-05-09 21:29:50.870 Enabling Settings Cache.
2007-05-09 21:29:50.870 Clearing Settings Cache.
2007-05-09 21:29:50.871 MSqlQuery: SELECT data FROM settings WHERE value = 'DBSchemaVer' AND hostname = 'p4ubuntu' ;
2007-05-09 21:29:50.871 MSqlQuery: SELECT data FROM settings WHERE value = 'DBSchemaVer' AND hostname IS NULL;
2007-05-09 21:29:50.871 Current Schema Version: 1160
2007-05-09 21:29:50.872 Clearing Settings Cache.
2007-05-09 21:29:50.872 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiVidModeResolution' AND hostname = 'p4ubuntu' ;
2007-05-09 21:29:50.873 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiVidModeResolution' AND hostname IS NULL;
2007-05-09 21:29:50.873 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiVidModeWidth' AND hostname = 'p4ubuntu' ;
2007-05-09 21:29:50.874 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiVidModeWidth' AND hostname IS NULL;
2007-05-09 21:29:50.874 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiVidModeHeight' AND hostname = 'p4ubuntu' ;
2007-05-09 21:29:50.874 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiVidModeHeight' AND hostname IS NULL;
2007-05-09 21:29:50.876 MSqlQuery: SELECT data FROM settings WHERE value = 'DisplaySizeResolution' AND hostname = 'p4ubuntu' ;
2007-05-09 21:29:50.876 MSqlQuery: SELECT data FROM settings WHERE value = 'DisplaySizeResolution' AND hostname IS NULL;
2007-05-09 21:29:50.877 MSqlQuery: SELECT data FROM settings WHERE value = 'DisplaySizeWidth' AND hostname = 'p4ubuntu' ;
2007-05-09 21:29:50.877 MSqlQuery: SELECT data FROM settings WHERE value = 'DisplaySizeWidth' AND hostname IS NULL;
2007-05-09 21:29:50.878 MSqlQuery: SELECT data FROM settings WHERE value = 'DisplaySizeHeight' AND hostname = 'p4ubuntu' ;
2007-05-09 21:29:50.878 MSqlQuery: SELECT data FROM settings WHERE value = 'DisplaySizeHeight' AND hostname IS NULL;
2007-05-09 21:29:50.879 MSqlQuery: SELECT data FROM settings WHERE value = 'TVVidModeResolution' AND hostname = 'p4ubuntu' ;
2007-05-09 21:29:50.879 MSqlQuery: SELECT data FROM settings WHERE value = 'TVVidModeResolution' AND hostname IS NULL;
2007-05-09 21:29:50.880 MSqlQuery: SELECT data FROM settings WHERE value = 'TVVidModeWidth' AND hostname = 'p4ubuntu' ;
2007-05-09 21:29:50.880 MSqlQuery: SELECT data FROM settings WHERE value = 'TVVidModeWidth' AND hostname IS NULL;
2007-05-09 21:29:50.881 MSqlQuery: SELECT data FROM settings WHERE value = 'TVVidModeHeight' AND hostname = 'p4ubuntu' ;
2007-05-09 21:29:50.881 MSqlQuery: SELECT data FROM settings WHERE value = 'TVVidModeHeight' AND hostname IS NULL;
2007-05-09 21:29:50.882 MSqlQuery: SELECT data FROM settings WHERE value = 'VidModeResolution0' AND hostname = 'p4ubuntu' ;
2007-05-09 21:29:50.882 MSqlQuery: SELECT data FROM settings WHERE value = 'VidModeResolution0' AND hostname IS NULL;
2007-05-09 21:29:50.883 MSqlQuery: SELECT data FROM settings WHERE value = 'VidModeWidth0' AND hostname = 'p4ubuntu' ;
2007-05-09 21:29:50.883 MSqlQuery: SELECT data FROM settings WHERE value = 'VidModeWidth0' AND hostname IS NULL;
2007-05-09 21:29:50.884 MSqlQuery: SELECT data FROM settings WHERE value = 'VidModeHeight0' AND hostname = 'p4ubuntu' ;
2007-05-09 21:29:50.884 MSqlQuery: SELECT data FROM settings WHERE value = 'VidModeHeight0' AND hostname IS NULL;
2007-05-09 21:29:50.884 MSqlQuery: SELECT data FROM settings WHERE value = 'TVVidModeResolution0' AND hostname = 'p4ubuntu' ;
2007-05-09 21:29:50.885 MSqlQuery: SELECT data FROM settings WHERE value = 'TVVidModeResolution0' AND hostname IS NULL;
2007-05-09 21:29:50.885 MSqlQuery: SELECT data FROM settings WHERE value = 'TVVidModeWidth0' AND hostname = 'p4ubuntu' ;
2007-05-09 21:29:50.886 MSqlQuery: SELECT data FROM settings WHERE value = 'TVVidModeWidth0' AND hostname IS NULL;
2007-05-09 21:29:50.886 MSqlQuery: SELECT data FROM settings WHERE value = 'TVVidModeHeight0' AND hostname = 'p4ubuntu' ;
2007-05-09 21:29:50.886 MSqlQuery: SELECT data FROM settings WHERE value = 'TVVidModeHeight0' AND hostname IS NULL;
<THEN THERE IS A CORE DUMP> [/INDENT]

Then I looked at the mysql table (settings) that the queries are in and it looks like this:
[INDENT]Server: localhost - Database: mythconverg - Table: settings

* BrowseBrowse
* StructureStructure
* SQLSQL
* SearchSearch
* InsertInsert
* ExportExport
* ImportImport
* OperationsOperations
* EmptyEmpty
* DropDrop



Showing rows 0 - 8 (9 total, Query took 0.0002 sec)
SQL query: SELECT *
FROM `settings`
ORDER BY `value` ASC , `hostname` ASC
LIMIT 0 , 30
[ Edit ] [ Explain SQL ] [ Create PHP Code ] [ Refresh ]

Query results operations Print viewPrint view Print view (with full texts)Print view (with full texts) ExportExport


row(s) starting from record #
in mode and repeat headers after cells

Sort by key:
Full Texts value data hostname
Edit Delete DataDirectMessage NULL NULL
Edit Delete DBSchemaVer 1160 NULL
Edit Delete DefaultTranscoder 0 NULL
Edit Delete HaveRepeats 0 NULL
Edit Delete mythfilldatabaseLastRunEnd NULL NULL
Edit Delete mythfilldatabaseLastRunStart NULL NULL
Edit Delete mythfilldatabaseLastRunStatus NULL NULL
Edit Delete MythFillGrabberSuggestsTime 1 NULL
Edit Delete MythFillSuggestedRunTime 1970-01-01T00:00:00 NULL
With selected: Check All / Uncheck All With selected: Change Delete Export


row(s) starting from record #
in mode and repeat headers after cells [/INDENT]

I hope that's not just too much garbage - hopefully someone can tell me what to do short of reinstalling ubuntu feisty!!!

Any, ANY, help would really be appreciate!

Thanks in advance,
Dave

---

### Post by newlinux on 2007-05-10
Well, I haven't seen this particular output, but I have seen a lot database corruption with mythtv. I'm not sure if this is happening with you but it's worth a try to reinstall the databases (since you said ANY help:)).
```

sudo apt-get remove --purge mythtv-database mysql-server-5.0
sudo apt-get install mysql-server-5.0 mythtv-database

```

will reinstall the database, if you haven't already tried this... Good luck.

---

### Post by ijustam on 2007-05-22
I am having the same problem with no resolution :(

---

### Post by electronikjunkie on 2007-05-22
i'd go w/newlinux, but do a little more just to be sure:

```
dpkg --get-selections|grep myth
```
now uninstall everything related to mythtv
```
sudo apt-get --purge remove mythpackageslistedabove
```
now remove the mythconverg database from mysql if it's there and remove your .mythtv directory:
```
mysql -uroot -p
>drop database mythconverg;
>quit
rm ~/.mythtv

```
now reinstall what you need, on a front/backend box i do this:
```
sudo apt-get install mythtv-database mythtv-backend mythtv-frontend mythtv-themes
```
after that add your user to the mythtv group:
```
sudo usermod -a -G mythtv youraccountname
```
now run setup:
```
mythtv-setup
```

hope this helps/works for you...

---

### Post by ijustam on 2007-05-22
Well, I got some different screens that time, but I still get the same segmentation fault.

```
Stopping MythTV server: mythbackend No /usr/bin/mythbackend found running; none killed.
.
2007-05-22 22:27:45.342 Using runtime prefix = /usr
2007-05-22 22:27:45.348 Gnome-Screensaver support enabled
2007-05-22 22:27:45.348 DPMS is active.
2007-05-22 22:27:45.357 New DB connection, total: 1
2007-05-22 22:27:45.361 Connected to database 'mythconverg' at host: localhost
2007-05-22 22:27:45.361 Total desktop dim: 2880x900, with 2 screen[s].
2007-05-22 22:27:45.363 Using screen 0, 1440x900 at 1440,0
2007-05-22 22:27:45.370 Current Schema Version: 1160
Segmentation fault (core dumped)
Restarting MythTV server: mythbackend No /usr/bin/mythbackend found running; none killed.
.
.

```

---

### Post by newlinux on 2007-05-22
what do your backend logs state?

What kind of video setup are you using?

---

### Post by ijustam on 2007-05-22
Thanks for your help!

This is my backend log output
```
2007-05-22 22:19:27.253 Using runtime prefix = /usr
2007-05-22 22:19:27.289 New DB connection, total: 1
2007-05-22 22:19:27.360 Unable to connect to database!
2007-05-22 22:19:27.369 Driver error was [1/1049]:
QMYSQL3: Unable to connect
Database error was:
Unknown database 'mythconverg'

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-05-22 22:19:27.473 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-05-22 22:19:27.532 Failed to init MythContext, exiting.
2007-05-22 22:25:43.833 Using runtime prefix = /usr
2007-05-22 22:25:43.859 New DB connection, total: 1
2007-05-22 22:25:43.863 Unable to connect to database!
2007-05-22 22:25:43.864 Driver error was [1/1049]:
QMYSQL3: Unable to connect
Database error was:
Unknown database 'mythconverg'

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-05-22 22:25:43.929 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-05-22 22:25:43.987 Failed to init MythContext, exiting.
2007-05-22 22:26:23.883 Using runtime prefix = /usr
2007-05-22 22:26:23.905 New DB connection, total: 1
2007-05-22 22:26:23.910 Connected to database 'mythconverg' at host: localhost
2007-05-22 22:26:23.917 Current Schema Version: 1160
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.
2007-05-22 22:26:37.860 Using runtime prefix = /usr
2007-05-22 22:26:37.885 New DB connection, total: 1
2007-05-22 22:26:37.889 Connected to database 'mythconverg' at host: localhost
2007-05-22 22:26:37.892 Current Schema Version: 1160
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.
2007-05-22 22:27:53.032 Using runtime prefix = /usr
2007-05-22 22:27:53.052 New DB connection, total: 1
2007-05-22 22:27:53.057 Connected to database 'mythconverg' at host: localhost
2007-05-22 22:27:53.059 Current Schema Version: 1160
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.
```

I am running an nVidia GeForce 7600 with dual 1440x900 displays using Xinerama.

---

### Post by newlinux on 2007-05-23
Have you changed this machine's hostname lately? What do you have the backend IP address set to? If localhost (127.0.0.1) then try running mythtv-setup as the mythtv user and change it to the machine's IP address. Also, what does your mysql.txt say the IP address is (all of them on your system)?

---

### Post by ijustam on 2007-05-23
The hostname has not been changed since I installed it.  However, Apache complains that it can't find my hostname, "apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName"  I can access phpMyAdmin and my Apache index no problem.

Setup will not run (my verbose output is pretty much verbatim of that in the original post- it just dies after a slew of SQL requests).  mysql.txt has my IP as localhost.

---

### Post by ijustam on 2007-05-23
I got it! :D

I think Xinerama had something to do with it.  I disabled one of my monitors and ran setup on a single monitor under mythtv and then re-enabled the monitor after setup, and both frontend and backend work correctly.

Thank you all for your help!

---

