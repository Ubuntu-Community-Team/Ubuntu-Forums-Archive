---
title: "Mythtv MasterBackend Problem"
date: 2007-02-16
forum: Multimedia &amp; Video
---

### Post by Chewiesw on 2007-02-16
I am experiecing a few problems with my Mythtv installation, I am trying to install a complete frontend , backend, desktop system. I am guessing that it all has to do with this error message 

**could not connect to the masterbackend server -- is it running? Is the IP address set for it in the setup program correct?**

I get this from the terminal

> X Error: BadDevice, invalid or uninitialized input device 168

Major opcode: 146

Minor opcode: 3

Resource id: 0x0

Failed to open device

X Error: BadDevice, invalid or uninitialized input device 168

Major opcode: 146

Minor opcode: 3

Resource id: 0x0

Failed to open device

2007-02-16 12:52:02.607 Using runtime prefix = /usr

2007-02-16 12:52:02.620 Gnome-Screensaver support enabled

2007-02-16 12:52:02.621 DPMS is active.

2007-02-16 12:52:02.661 New DB connection, total: 1

2007-02-16 12:52:02.667 Connected to database 'mythconverg' at host: localhost

2007-02-16 12:52:02.670 Total desktop dim: 1280x1024, with 1 screen[s].

2007-02-16 12:52:02.730 Using screen 0, 1280x1024 at 0,0

2007-02-16 12:52:02.852 Current Schema Version: 1160

2007-02-16 12:52:02.852 mythfrontend version: 0.20.20060828-3 [www.mythtv.org](www.mythtv.org)

2007-02-16 12:52:02.853 Enabled verbose msgs: important general

2007-02-16 12:52:03.821 Total desktop dim: 1280x1024, with 1 screen[s].

2007-02-16 12:52:03.823 Using screen 0, 1280x1024 at 0,0

2007-02-16 12:52:03.824 Switching to square mode (Titivillus) libGL warning: 3D driver claims to not support visual 0x4b

2007-02-16 12:52:04.025 Using the Qt painter

mythtv: could not open config file /home/mythtv/.mythtv/lircrc

mythtv: No such file or directory

Failed to read lirc config /home/mythtv/.mythtv/lircrc for mythtv

2007-02-16 12:52:04.407 Joystick disabled.

2007-02-16 12:52:04.596 Loading from: /usr/share/mythtv/themes/default/base.xml

2007-02-16 12:52:05.012 Registering Internal as a media playback plugin.

2007-02-16 13:14:24.497 XMLParse::LoadTheme using /usr/share/mythtv/themes/Titivillus/ui.xml

2007-02-16 13:14:25.196 GuideGrid:

You don't have any channels defined in the database.

Guide grid will have nothing to show you.

2007-02-16 13:14:25.203 Connecting to backend server: 127.0.0.1:6543 (try 1 of

5)

2007-02-16 13:14:25.204 Connection timed out.

You probably should modify the Master Server

settings in the setup program and set the

proper IP address.

2007-02-16 13:15:42.535 ProgramList::FromScheduler(): Error querying master.

Segmentation fault (core dumped)

$
I have tried using both the loopback address and the actual IP address of the server with no luck.


After I do a

sudo /etc/init.d/mythtv-backend restart

and

ps -p `cat /var/run/mythtv/mythbackend.pid`
All I get is
PID TTY          TIME CMD

Which would indicate to me that the process is not running.
I am also having trouble with my remote is doesn't work in Myth but I see output in the terminal with IRW, having a look around i can't seem to see a lircrc file anywhere. Is this problem aslo related to the backend server?

---

### Post by superm1 on 2007-02-16
> **Chewiesw said:**
> I am experiecing a few problems with my Mythtv installation, I am trying to install a complete frontend , backend, desktop system. I am guessing that it all has to do with this error message 

**could not connect to the masterbackend server -- is it running? Is the IP address set for it in the setup program correct?**

I get this from the terminal


I have tried using both the loopback address and the actual IP address of the server with no luck.


After I do a

sudo /etc/init.d/mythtv-backend restart

and

ps -p `cat /var/run/mythtv/mythbackend.pid`
All I get is
PID TTY          TIME CMD

Which would indicate to me that the process is not running.
I am also having trouble with my remote is doesn't work in Myth but I see output in the terminal with IRW, having a look around i can't seem to see a lircrc file anywhere. Is this problem aslo related to the backend server?
Well if this process isn't running, then check /var/log/mythtv/mythbackend.log.  It should say why (hopefully) it isn't running anymore or couldn't run.

The most common cause is permissions on the directory that it is trying to write recordings to.  The mythtv user or mythtv group need permissions.

---

### Post by Chewiesw on 2007-02-16
This is my backend log

> 2007-02-16 07:36:04.768 MainServer::HandleAnnounce Monitor
2007-02-16 07:36:04.783 adding: pvrbox as a client (events: 0)
2007-02-16 07:36:04.785 MainServer::HandleAnnounce Monitor
2007-02-16 07:36:04.786 adding: pvrbox as a client (events: 1)
2007-02-16 12:14:32.882 MainServer::HandleAnnounce Monitor
2007-02-16 12:14:32.886 adding: pvrbox as a client (events: 0)
2007-02-16 12:14:32.887 MainServer::HandleAnnounce Monitor
2007-02-16 12:14:32.889 adding: pvrbox as a client (events: 1)
2007-02-16 12:14:57.145 MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 1, exiting
2007-02-16 18:11:37.565 Using runtime prefix = /usr
2007-02-16 18:11:37.973 New DB connection, total: 1
2007-02-16 18:11:38.011 Unable to connect to database!
2007-02-16 18:11:38.067 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-02-16 18:11:38.234 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-02-16 18:11:38.294 Failed to init MythContext, exiting.

I guess this is the problem
Access denied for user 'mythtv'@'localhost' (using password: YES)

I have tried to follow the troubleshooting guide regarding mysql passwords, which I thought I had resolved (maybe NOT) I must admit I was a little confused with it.

---

### Post by superm1 on 2007-02-16
> **Chewiesw said:**
> This is my backend log



I guess this is the problem
Access denied for user 'mythtv'@'localhost' (using password: YES)

I have tried to follow the troubleshooting guide regarding mysql passwords, which I thought I had resolved (maybe NOT) I must admit I was a little confused with it.
This normally doesn't happen for the "mythtv" user based on what troubles people have been running into.  
Can you check the contents of /etc/mythtv/mysql.txt and /home/mythtv/.mythtv/mysql.txt

Compare the two.

---

### Post by Chewiesw on 2007-02-17
/etc/mythtv/mysql.txt

> DBHostName=localhost
DBUserName=mythtv
DBName=mythconverg
DBPassword=mythtv

~/.mythytv/mysql

> DBHostName=localhost
DBUserName=mythtv
DBPassword=mythtv
DBName=mythconverg
DBType=QMYSQL3

Does / will the DBType have any impact ?

---

