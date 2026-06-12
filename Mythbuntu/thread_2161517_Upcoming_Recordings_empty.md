---
title: "Upcoming Recordings empty"
date: 2013-07-11
forum: Mythbuntu
---

### Post by waynelivingstone on 2013-07-11
I've been setting up a new install of Mythbuntu 12.04 and had it almost done except for some tuner issues that I've been working through. 

I've been too busy to work on it for a while so I left it running but at some point I disconnected the ethernet cable. When I came back to work on it I found that no recordings have been happening but all the schedules are still there. The Upcoming Recordings is empty and in MythWeb it shows:

**Warning** at /usr/share/mythtv/mythweb/modules/tv/upcoming.php, line 91:
!!NoTrans: Invalid argument supplied for foreach()!!

I have tried the mysqlcheck with no effect and even tried restoring a database backup with no improvement too. 

I am not sure what to do now.

---

### Post by tgm4883 on 2013-07-11
Do you actually have guide data?

---

### Post by waynelivingstone on 2013-07-13
I dont have any guide data because the box has been turned off for 3 weeks, but the grabber isnt working now either. 
I have run the grabber a couple of times and even deleted it and reinstalled but it still dosnt run properly. It ends with this:

Posting anonymous usage statistics.
Done.
2013-07-13 04:22:14.963420 C  mythfilldatabase version: fixes/0.25 [v0.25.2-15-g46cab93] [www.mythtv.org](www.mythtv.org)
2013-07-13 04:22:14.963432 C  Qt version: compile: 4.8.1, runtime: 4.8.1
2013-07-13 04:22:14.963435 N  Enabled verbose msgs:  general
2013-07-13 04:22:14.963447 N  Setting Log Level to LOG_INFO
2013-07-13 04:22:14.963472 I  Added logging to the console
2013-07-13 04:22:14.963476 I  Added database logging to table logging
2013-07-13 04:22:14.963512 N  Setting up SIGHUP handler
2013-07-13 04:22:14.963553 I  Bypassing grabbers, reading directly from file
2013-07-13 04:22:14.963595 N  Using runtime prefix = /usr
2013-07-13 04:22:14.963837 N  Using configuration directory = /root/.mythtv
2013-07-13 04:22:14.964172 I  Assumed character encoding: en_AU.UTF-8
2013-07-13 04:22:14.964273 E  Error parsing: /root/.mythtv/config.xml at line: 1  column: 1
2013-07-13 04:22:14.964277 E  Error Msg: unexpected end of file
2013-07-13 04:22:14.964317 E  Unable to read configuration file mysql.txt
2013-07-13 04:22:14.964340 E  Error parsing: /root/.mythtv/config.xml at line: 1  column: 1
2013-07-13 04:22:14.964343 E  Error Msg: unexpected end of file
2013-07-13 04:22:14.964365 E  DBHostName is not set in config.xml
2013-07-13 04:22:14.964374 N  Empty LocalHostName.
2013-07-13 04:22:14.964378 I  Using localhost value of Myth-TV
2013-07-13 04:22:14.964404 E  Error parsing: /root/.mythtv/config.xml at line: 1  column: 1
2013-07-13 04:22:14.964407 E  Error Msg: unexpected end of file
2013-07-13 04:22:14.971995 E  Unable to connect to database!
2013-07-13 04:22:14.972020 E  Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)


No UPnP backends found

Would you like to configure the database connection now? [no]  2013-07-13 04:22:17.147343 I  UPnPautoconf() - No UPnP backends found
2013-07-13 04:22:17.147352 A  No UPnP backends found


It seems to me that the underlying problem is elsewhere. 

I have done a google search and found a couple of results that seem similar to my problem but understand the solutions: 

[http://www.mythtv.org/pipermail/mythtv-users/2013-January/345218.html](http://www.mythtv.org/pipermail/mythtv-users/2013-January/345218.html)

[http://code.mythtv.org/trac/ticket/10142](http://code.mythtv.org/trac/ticket/10142)

Can anyone point me in the right direction with some dumbed down instructions?

---

### Post by tgm4883 on 2013-07-13
> **waynelivingstone said:**
> I dont have any guide data because the box has been turned off for 3 weeks, but the grabber isnt working now either. 
I have run the grabber a couple of times and even deleted it and reinstalled but it still dosnt run properly. It ends with this:

Posting anonymous usage statistics.
Done.
2013-07-13 04:22:14.963420 C  mythfilldatabase version: fixes/0.25 [v0.25.2-15-g46cab93] [www.mythtv.org](www.mythtv.org)
2013-07-13 04:22:14.963432 C  Qt version: compile: 4.8.1, runtime: 4.8.1
2013-07-13 04:22:14.963435 N  Enabled verbose msgs:  general
2013-07-13 04:22:14.963447 N  Setting Log Level to LOG_INFO
2013-07-13 04:22:14.963472 I  Added logging to the console
2013-07-13 04:22:14.963476 I  Added database logging to table logging
2013-07-13 04:22:14.963512 N  Setting up SIGHUP handler
2013-07-13 04:22:14.963553 I  Bypassing grabbers, reading directly from file
2013-07-13 04:22:14.963595 N  Using runtime prefix = /usr
2013-07-13 04:22:14.963837 N  Using configuration directory = /root/.mythtv
2013-07-13 04:22:14.964172 I  Assumed character encoding: en_AU.UTF-8
2013-07-13 04:22:14.964273 E  Error parsing: /root/.mythtv/config.xml at line: 1  column: 1
2013-07-13 04:22:14.964277 E  Error Msg: unexpected end of file
2013-07-13 04:22:14.964317 E  Unable to read configuration file mysql.txt
2013-07-13 04:22:14.964340 E  Error parsing: /root/.mythtv/config.xml at line: 1  column: 1
2013-07-13 04:22:14.964343 E  Error Msg: unexpected end of file
2013-07-13 04:22:14.964365 E  DBHostName is not set in config.xml
2013-07-13 04:22:14.964374 N  Empty LocalHostName.
2013-07-13 04:22:14.964378 I  Using localhost value of Myth-TV
2013-07-13 04:22:14.964404 E  Error parsing: /root/.mythtv/config.xml at line: 1  column: 1
2013-07-13 04:22:14.964407 E  Error Msg: unexpected end of file
2013-07-13 04:22:14.971995 E  Unable to connect to database!
2013-07-13 04:22:14.972020 E  Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)


No UPnP backends found

Would you like to configure the database connection now? [no]  2013-07-13 04:22:17.147343 I  UPnPautoconf() - No UPnP backends found
2013-07-13 04:22:17.147352 A  No UPnP backends found


It seems to me that the underlying problem is elsewhere. 

I have done a google search and found a couple of results that seem similar to my problem but understand the solutions: 

[http://www.mythtv.org/pipermail/mythtv-users/2013-January/345218.html](http://www.mythtv.org/pipermail/mythtv-users/2013-January/345218.html)

[http://code.mythtv.org/trac/ticket/10142](http://code.mythtv.org/trac/ticket/10142)

Can anyone point me in the right direction with some dumbed down instructions?


Why are you running mythfilldatabase as root?

---

### Post by waynelivingstone on 2013-07-13
I know its not ideal to run mythfilldatabase as root but it used to be the only way I could get it to run properly and I've just kept doing it that way. It's never caused me any problems.

---

### Post by tgm4883 on 2013-07-14
> **waynelivingstone said:**
> I know its not ideal to run mythfilldatabase as root but it used to be the only way I could get it to run properly and I've just kept doing it that way.** It's never caused me any problems.**

Are you sure?

> **waynelivingstone said:**
> 
2013-07-13 04:22:14.963837 **N  Using configuration directory = /root/.mythtv**
2013-07-13 04:22:14.964172 I  Assumed character encoding: en_AU.UTF-8
2013-07-13 04:22:14.964273 **E  Error parsing: /root/.mythtv/config.xml at line: 1  column: 1**
2013-07-13 04:22:14.964277 **E  Error Msg: unexpected end of file**
2013-07-13 04:22:14.964317 **E  Unable to read configuration file mysql.txt**
2013-07-13 04:22:14.964340 E  Error parsing: /root/.mythtv/config.xml at line: 1  column: 1
2013-07-13 04:22:14.964343 E  Error Msg: unexpected end of file
2013-07-13 04:22:14.964365 E  DBHostName is not set in config.xml
2013-07-13 04:22:14.964374 N  Empty LocalHostName.
2013-07-13 04:22:14.964378 I  Using localhost value of Myth-TV
2013-07-13 04:22:14.964404 E  Error parsing: /root/.mythtv/config.xml at line: 1  column: 1
2013-07-13 04:22:14.964407 E  Error Msg: unexpected end of file
2013-07-13 04:22:14.971995 **E  Unable to connect to database!**
2013-07-13 04:22:14.972020 E  Driver error was [1/1045]:
[B]QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)[/B]


Seems to me that you running it as root is causing you problems now.

---

### Post by waynelivingstone on 2013-07-15
That's really weird, it was running fine as root for weeks before this happened. 

Anyway I'm running it as my user now and it seem to be working now so far.

---

