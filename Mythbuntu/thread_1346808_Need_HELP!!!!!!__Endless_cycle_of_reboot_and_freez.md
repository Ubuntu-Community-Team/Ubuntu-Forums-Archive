---
title: "Need HELP!!!!!!  Endless cycle of reboot and freezeup....."
date: 2009-12-05
forum: Mythbuntu
---

### Post by sawbuck on 2009-12-05
Really need help getting back into my Mythtv system.  I'm running Mythbuntu 9.04 with 9,04 Ubuntu desktop as an addon.
 
I had to (physically) move my network router which reset the IP address for the mythbox and other computers on my homenet.  (Maybe I should not have powered them all down...)  In the past I've had that problem after power loss and it was simply a matter of correcting the IP addresses in the frontend and backend so the database could be found on the myth box after powering up.  I don't recall what sequence I did it in the past but I think it us usually evident when starting the front end so likely that was done first.
 
Anyway, when I turned the system on it tried to open up into MythTV but could find the database (it went into language setup followwed by frontend setup) so I exited and checked the address of eth0 and reopened mythfrontend and added it hitting "next" until I was back into the top myth menu.  I'm not sure but I think it hung at the top menu when I tried to "ESC" out to the desktop.
 
At any rate, I am now in an endless cycle of rebooting, then it tries to open the friontend and goes to a black screen and stays that way for about 5 minutes then goes to the frontend main menu an displays a message saying it is unable to find the database.  No matter if I "ok" out of that or "ESC" out it locks up to a black screen and stays there.
 
I've tried "Ctrl +Alt +F1" and going into "mythtv-setup" but a "Zenity" GKT something-or-other message says it can't open the display.
 
Soooo, since I can only DO anything in the command window, how do I override the display problem and get into mythtv setup and make the database IP pointers match? 
Unless there is some way into a desktop the only way into the system is the terminal window.  Likely obvious to all....
 
I can't find threads with any hints to a solution so any help is appreciated....

---

### Post by sawbuck on 2009-12-05
Well, guess I should have waited longer.  After about 30 minutes the freeze unfroze.  The "ESC" I hit the last time it froze just before stomping off to another PC to post the original message finally showed the confirmation screen to exit MythTV back to the desktop while I was on the phone at the myth box asking assistance from another myth user.  I was able to get back into backend setup and reset the IP addresses to match and now I'm almost back in business.

However, when I went to "mythfilldatabase" it was unable to complete with this in the backend log:

```
2009-12-05 14:13:10.388 Scheduled 6 items in 0.2 = 0.09 match + 0.08 place
2009-12-05 14:13:10.432 scheduler: Scheduled items: Scheduled 6 items in 0.2 = 0.09 match + 0.08 place
2009-12-05 14:13:10.476 Seem to be woken up by USER
2009-12-05 14:13:17.212 mythbackend: Running housekeeping thread
2009-12-05 14:13:17.314 UPnpMedia: BuildMediaMap - no VideoStartupDir set,  skipping scan.
2009-12-05 14:14:27.219 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-12-05 14:17:02.078 MainServer::ANN Monitor
2009-12-05 14:17:02.167 adding: Frank4 as a client (events: 0)
2009-12-05 14:22:33.340 MainServer::ANN Monitor
2009-12-05 14:22:33.423 adding: Frank4 as a client (events: 0)
2009-12-05 14:22:33.474 MainServer::ANN Monitor
2009-12-05 14:22:33.523 adding: Frank4 as a client (events: 1)
2009-12-05 14:22:48.659 Reloading backend settings
2009-12-05 14:29:27.407 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-12-05 14:30:52.557 mythbackend version: branches/release-0-22-fixes [22594] www.mythtv.org
2009-12-05 14:30:52.820 Using runtime prefix = /usr
2009-12-05 14:30:53.016 Using configuration directory = /home/mythtv/.mythtv
2009-12-05 14:30:53.512 Empty LocalHostName.
2009-12-05 14:30:53.690 Using localhost value of Frank4
2009-12-05 14:30:54.050 Testing network connectivity to '192.168.1.101'
2009-12-05 14:30:54.231 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2009-12-05 14:30:54.276 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
SSDP::PerformSearch - did not write entire buffer.2009-12-05 14:30:54.431 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error

SSDP::PerformSearch - did not write entire buffer.
..............................................................
2009-12-05 14:30:57.259 UPnPautoconf() - No UPnP backends found
2009-12-05 14:30:57.333 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2009-12-05 14:30:57.896 Deleting UPnP client...
2009-12-05 14:30:58.311 Failed to init MythContext, exiting.
2009-12-05 14:30:59.256 mythbackend version: branches/release-0-22-fixes [22594] www.mythtv.org
2009-12-05 14:30:59.363 Using runtime prefix = /usr
2009-12-05 14:30:59.430 Using configuration directory = /home/mythtv/.mythtv
2009-12-05 14:30:59.497 Empty LocalHostName.
2009-12-05 14:30:59.556 Using localhost value of Frank4
2009-12-05 14:30:59.606 Testing network connectivity to '192.168.1.101'
2009-12-05 14:30:59.741 New DB connection, total: 1
2009-12-05 14:30:59.882 Connected to database 'mythconverg' at host: 192.168.1.101
2009-12-05 14:30:59.955 Closing DB connection named 'DBManager0'
2009-12-05 14:31:00.015 Connected to database 'mythconverg' at host: 192.168.1.101
2009-12-05 14:31:00.078 Current MythTV Schema Version (DBSchemaVer): 1244
2009-12-05 14:31:00.119 MythBackend: Starting up as the master server.
2009-12-05 14:31:00.362 New DB connection, total: 2
2009-12-05 14:31:00.434 Connected to database 'mythconverg' at host: 192.168.1.101
2009-12-05 14:31:00.480 mythbackend: MythBackend started as master server
2009-12-05 14:31:00.775 New DB connection, total: 3
2009-12-05 14:31:00.829 Connected to database 'mythconverg' at host: 192.168.1.101
2009-12-05 14:31:01.128 New DB scheduler connection
2009-12-05 14:31:01.187 Connected to database 'mythconverg' at host: 192.168.1.101
2009-12-05 14:31:01.251 Scheduler, Warning: Listings source '' is defined, but is not attached to a card input.
2009-12-05 14:31:01.453 Enabling Upnpmedia rebuild thread.
2009-12-05 14:31:02.775 Main::Registering HttpStatus Extension
2009-12-05 14:31:02.854 Enabled verbose msgs:  important general
2009-12-05 14:31:02.928 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-12-05 14:31:04.360 Reschedule requested for id -1.
2009-12-05 14:31:04.506 DB Error (UpdateMatches):
Query was:
DELETE FROM program WHERE manualid <> 0
Driver error was [2/1194]:
QMYSQL3: Unable to execute statement
Database error was:
Table 'program' is marked as crashed and should be repaired

2009-12-05 14:31:05.681 Scheduled 6 items in 1.2 = 0.23 match + 1.02 place
2009-12-05 14:31:05.779 scheduler: Scheduled items: Scheduled 6 items in 1.2 = 0.23 match + 1.02 place
2009-12-05 14:31:05.955 Seem to be woken up by USER
2009-12-05 14:31:11.333 mythbackend: Running housekeeping thread
2009-12-05 14:31:11.516 UPnpMedia: BuildMediaMap - no VideoStartupDir set,  skipping scan.
2009-12-05 14:31:12.007 MainServer::ANN Monitor
2009-12-05 14:31:12.049 adding: Frank4 as a client (events: 0)
2009-12-05 14:31:12.092 MainServer::ANN Monitor
2009-12-05 14:31:12.133 adding: Frank4 as a client (events: 1)
2009-12-05 14:32:21.343 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-12-05 14:34:58.006 MainServer::ANN Monitor
2009-12-05 14:34:58.065 adding: Frank4 as a client (events: 0)
2009-12-05 14:34:58.108 MainServer::ANN Monitor
2009-12-05 14:34:58.148 adding: Frank4 as a client (events: 1)
2009-12-05 14:34:58.209 Reschedule requested for id -1.
2009-12-05 14:34:58.269 DB Error (UpdateMatches):
Query was:
DELETE FROM program WHERE manualid <> 0
Driver error was [2/1194]:
QMYSQL3: Unable to execute statement
Database error was:
[COLOR=Red]Table 'program' is marked as crashed and should be repaired[/COLOR]

2009-12-05 14:34:58.405 Scheduled 6 items in 0.2 = 0.10 match + 0.09 place
2009-12-05 14:34:58.457 scheduler: Scheduled items: Scheduled 6 items in 0.2 = 0.10 match + 0.09 place
2009-12-05 14:35:59.687 MainServer::ANN Monitor
2009-12-05 14:35:59.733 adding: Frank4 as a client (events: 0)
2009-12-05 14:35:59.776 MainServer::ANN Monitor
2009-12-05 14:35:59.825 adding: Frank4 as a client (events: 1)
2009-12-05 14:48:21.249 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

```

How do I repair the "Table 'program'?

---

### Post by sawbuck on 2009-12-06
Still can't finish a schedules direct "mythfilldatabase".  No information in the program grid either - nada.  How can repair the table named in this error messge:

Table 'program' is marked as crashed and should be repaired

---

### Post by blackoper on 2009-12-06
there is a database repair page in mythweb to repair the database. It's in the setup/settings section of it. That's how I repaired it last time. Also in mythbuntu control center there is a checkmark in it to do a daily check of the mysql tables. I don't remember the command in the terminal to do it directly. 

Edit:
Looked the command up:
mysqlcheck --auto-repair mythconverg  (that may be it or it may need -u mythtv -p added)

---

### Post by sawbuck on 2009-12-06
> **blackoper said:**
> there is a database repair page in mythweb to repair the database. It's in the setup/settings section of it. That's how I repaired it last time. Also in mythbuntu control center there is a checkmark in it to do a daily check of the mysql tables. I don't remember the command in the terminal to do it directly. 

Edit:
Looked the command up:
mysqlcheck --auto-repair mythconverg  (that may be it or it may need -u mythtv -p added)

blackoper,

Thanks for replying with the help.  I did as sugggested but when I execute it - either as root or otherwise - I get an error such as:

```
frank@Frank4:~$ sudo mysqlcheck --auto-repair mythconverg  --password=T3Nas9sf
mysqlcheck: Got error: 1045: Access denied for user 'root'@'localhost' (using password: YES) when trying to connect
```

The Password is that which is used to access the database from the FE/BE unit or other FE only units - which work.  Is there another password?  If so I don't remember adding it or how to find it.

With the alternate suggestion of -u & -p the same error:

f```
rank@Frank4:~$ sudo mysqlcheck --auto-repair mythconverg -u=mythtv -p=T3Nas9sf
mysqlcheck: Got error: 1045: Access denied for user '=mythtv'@'localhost' (using password: YES) when trying to connect
```

I get the same error if I just use -c to just check it.

I did set up the daily check in MCC.  It didn't ask for a password so it will be intersting to see what happens.  I'll check tomorrow but don't expect much....

---

### Post by sawbuck on 2009-12-08
Well, finally found how to get into mythweb.  I looked all over the menus - both on the desktop and mythTV - and didn't see it but good old google found the way.

Anyway, I still couldn't - as ofyesterday - see any data in the program guide and mythfilldatabase was still reporting a crashed file table.  This morning, after finding how to get on mytheb, I saw the "repair table" tab and hit it.  Not sure if that fixed it or if the MCC setting done earlier did but now all is well.....  Will have to look at logs to see history,,,

---

