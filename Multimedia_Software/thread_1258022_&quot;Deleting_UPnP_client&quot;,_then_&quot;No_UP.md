---
title: "&quot;Deleting UPnP client&quot;, then &quot;No UPnP backends found&quot;"
date: 2009-09-04
forum: Multimedia Software
---

### Post by NinjaNumberNine on 2009-09-04
Hi, another problem with setting up mythtv... :sigh: 
Anyway,  I install mythtv and in terminal type "mythtv". It loads the "Select your language" screen and I press enter and it says: "No UPnP backends found".
Now, I looked in terminal at the output, and I find that it DELETES the upnp backend right before it says the error! Strange.... Can someone help please? I have had this problem before, but I forgot how I fixed it, some sort of terminal command... I really want to get this working. 
Here's the terminal output:
```
halstan@Victory:~$ mythtv
2009-09-04 13:11:08.098 Using runtime prefix = /usr
2009-09-04 13:11:08.109 XScreenSaver support enabled
2009-09-04 13:11:08.109 DPMS is active.
2009-09-04 13:11:08.114 Empty LocalHostName.
2009-09-04 13:11:08.114 Using localhost value of Victory
2009-09-04 13:11:08.126 New DB connection, total: 1
2009-09-04 13:11:08.133 Unable to connect to database!
2009-09-04 13:11:08.133 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-09-04 13:11:08.184 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QServerSocket: failed to bind or listen to the socket
2009-09-04 13:11:08.235 MCP::InitUPnP() - HttpServer Create Error
2009-09-04 13:11:08.235 [COLOR=Red]**Deleting UPnP client...**[/COLOR]
2009-09-04 13:11:08.236** [COLOR=DarkRed]No UPnP backends found[/COLOR]**
2009-09-04 13:11:08.671 max_width: 1360 max_height: 864
2009-09-04 13:11:08.673 Primary screen 0.
2009-09-04 13:11:08.673 Using screen 0, 1152x864 at 0,0
2009-09-04 13:11:08.673 No theme dir: /home/halstan/.mythtv/themes/blue
2009-09-04 13:11:08.674 Switching to square mode (blue)
get fences failed: -1
param: 6, val: 0
2009-09-04 13:11:08.757 Using the Qt painter
2009-09-04 13:11:08.757 JoystickMenuClient Error: Joystick disabled - Failed to read /home/halstan/.mythtv/joystickmenurc
mythtv: could not connect to socket
mythtv: No such file or directory
2009-09-04 13:11:08.768 lirc_init failed for mythtv, see preceding messages
```


 Thanks in advance!

---

### Post by NinjaNumberNine on 2009-09-04
bump


I'd like to get this done today, if possible! [-o<

---

### Post by NinjaNumberNine on 2009-09-04
Okay, you guys seem to use this strategy: "Don't reply for at least a day and maybe he'll figure it out himself without our help." Not sure I like it, but it DOES work. I got this thing fixed again by the following commands:
```
sudo apt-get remove libqt3-mt-mysql
```

then, seing that the previous removed mythtv as well, I type
```
sudo apt-get install mythtv
```
then get the mysql back by 
```
sudo apt-get install libqt3-mt-mysql
```
 and what do you know, Now I run the MythTV Backend Setup and it still says no UPnP backends found but don't leave: I press enter, go through the 2 config screens, and BAM, MythTV Backend loads, and everything works great! 
I hope this helps someone, and I was just kidding about the strategy. There is great support here, even though sometimes a post is not answered for a while.

Thanks, everyone!

---

