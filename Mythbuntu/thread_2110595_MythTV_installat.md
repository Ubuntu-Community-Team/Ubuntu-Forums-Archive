---
title: "MythTV installat"
date: 2013-01-30
forum: Mythbuntu
---

### Post by mr_si on 2013-01-30
Myth TV Backend installation woes

So I've installed,unistalled and reinstalled mythtv backend. 2nd time around

* MythTV backend setup crashes on the first setup screen (freezes at Where Are You?) (There are no languages listed?)
* The OS now asks me if I want to run mythtv backend.Yes. (permissions). Would I like to run mythfilldatabase? Yes

2013-01-30 21:19:29.423923 C  mythfilldatabase version: fixes/0.25 [v0.25.2-15-g46cab93] [www.mythtv.org]("http://www.mythtv.org")
2013-01-30 21:19:29.423961 C  Qt version: compile: 4.8.1, runtime: 4.8.1
2013-01-30 21:19:29.423972 N  Enabled verbose msgs:  general
2013-01-30 21:19:29.424005 N  Setting Log Level to LOG_INFO
2013-01-30 21:19:29.424078 I  Added logging to the console
2013-01-30 21:19:29.424093 I  Added database logging to table logging
2013-01-30 21:19:29.424214 N  Setting up SIGHUP handler
2013-01-30 21:19:29.424349 N  Using runtime prefix = /usr
2013-01-30 21:19:29.424373 N  Using configuration directory = /home/simon/.mythtv
2013-01-30 21:19:29.424603 I  Assumed character encoding: en_GB.UTF-8
2013-01-30 21:19:29.425013 N  Empty LocalHostName.
2013-01-30 21:19:29.425026 I  Using localhost value of lappy

Cannot login to database?

Would you like to configure the database connection now? [no]  2013-01-30 21:19:29.436653 E  Unable to connect to database!
2013-01-30 21:19:29.436690 E  Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

2013-01-30 21:19:29.436744 A  Cannot login to database?

2013-01-30 21:19:29.607114 E  Failed to init MythContext, exiting.
2013-01-30 21:19:29.608233 I  DataDirect: Deleting temporary files

simon@lappy:~$ sudo dpkg-reconfigure mythtv-database
[sudo] password for simon: 
Package `mythtv-database' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: mythtv-database is not installed.



Any thoughts? Kubuntu 12.04

---

### Post by tgm4883 on 2013-01-31
> **mr_si said:**
> Myth TV Backend installation woes

So I've installed,unistalled and reinstalled mythtv backend. 2nd time around

* MythTV backend setup crashes on the first setup screen (freezes at Where Are You?) (There are no languages listed?)
* The OS now asks me if I want to run mythtv backend.Yes. (permissions). Would I like to run mythfilldatabase? Yes

2013-01-30 21:19:29.423923 C  mythfilldatabase version: fixes/0.25 [v0.25.2-15-g46cab93] [www.mythtv.org]("http://www.mythtv.org")
2013-01-30 21:19:29.423961 C  Qt version: compile: 4.8.1, runtime: 4.8.1
2013-01-30 21:19:29.423972 N  Enabled verbose msgs:  general
2013-01-30 21:19:29.424005 N  Setting Log Level to LOG_INFO
2013-01-30 21:19:29.424078 I  Added logging to the console
2013-01-30 21:19:29.424093 I  Added database logging to table logging
2013-01-30 21:19:29.424214 N  Setting up SIGHUP handler
2013-01-30 21:19:29.424349 N  Using runtime prefix = /usr
2013-01-30 21:19:29.424373 N  Using configuration directory = /home/simon/.mythtv
2013-01-30 21:19:29.424603 I  Assumed character encoding: en_GB.UTF-8
2013-01-30 21:19:29.425013 N  Empty LocalHostName.
2013-01-30 21:19:29.425026 I  Using localhost value of lappy

Cannot login to database?

Would you like to configure the database connection now? [no]  2013-01-30 21:19:29.436653 E  Unable to connect to database!
2013-01-30 21:19:29.436690 E  Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

2013-01-30 21:19:29.436744 A  Cannot login to database?

2013-01-30 21:19:29.607114 E  Failed to init MythContext, exiting.
2013-01-30 21:19:29.608233 I  DataDirect: Deleting temporary files

simon@lappy:~$ sudo dpkg-reconfigure mythtv-database
[sudo] password for simon: 
Package `mythtv-database' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: mythtv-database is not installed.



Any thoughts? Kubuntu 12.04

Do you have mythtv-database installed (appears not), which means you've installed just mythtv-backend (instead of mythtv-backend-master).

---

