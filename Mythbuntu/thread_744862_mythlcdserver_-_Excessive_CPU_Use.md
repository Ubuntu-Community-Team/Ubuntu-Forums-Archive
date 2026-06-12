---
title: "mythlcdserver - Excessive CPU Use"
date: 2008-04-04
forum: Mythbuntu
---

### Post by whoisvince on 2008-04-04
I'm having a curious problem with my Mythbuntu 8.04 beta AMD64 install.  I updated a few days ago, and for the most part, everything went well.  The problem I am having now is with mythlcdserver.  I have an IMON VFD in an Antec Fusion case set up with lirc and lcdproc.  Mythlcdserver performed fine in Mythbuntu 7.10 (around 2% or so CPU use), but now it hits the processor very hard, usually around 30% CPU use, sometimes reaching 50% CPU use! 

The LCD displays information perfectly as it always has, but I am concerned about the excessive CPU usage, as it slows down playback when my processor gets really busy (encoding multiple video streams, bittorrent, etc).  I have an Athlon 64 X2 3600+, 1GB RAM, PVR-500 MCE and Pinnacle HDTV PCI 800i.  The machine functions as a backend/frontend with no other clients and no other desktop programs running (I disabled gnome/xfce)

Has anyone else seen a change in mythlcdserver CPU use since upgrading from MythTV 0.20.2/Mythbuntu 7.10 to MythTV 0.21/Mythbuntu 8.04?

Here's my mythlcdserver logfile:
```
2008-04-04 00:23:15.699 Using runtime prefix = /usr, libdir = /usr/lib
2008-04-04 00:23:15.802 Empty LocalHostName.
2008-04-04 00:23:15.802 Using localhost value of mythbox
2008-04-04 00:23:15.822 MCP::DefaultUPnP() - No default UPnP backend
2008-04-04 00:23:16.066 New DB connection, total: 1
2008-04-04 00:23:16.175 Connected to database 'mythconverg' at host: localhost
2008-04-04 00:23:16.179 Closing DB connection named 'DBManager0'
2008-04-04 00:23:16.179 Clearing Settings Cache.
2008-04-04 00:23:16.179 Enabling Settings Cache.
2008-04-04 00:23:16.180 Clearing Settings Cache.
2008-04-04 00:23:16.180 Connected to database 'mythconverg' at host: localhost
2008-04-04 00:23:16.195 MSqlQuery: SELECT data FROM settings WHERE value = 'MasterServerIP' AND hostname = 'mythbox' ;
2008-04-04 00:23:16.195 MSqlQuery: SELECT data FROM settings WHERE value = 'MasterServerIP' AND hostname IS NULL;
2008-04-04 00:23:16.196 MSqlQuery: SELECT data FROM settings WHERE value = 'MasterServerPort' AND hostname = 'mythbox' ;
2008-04-04 00:23:16.196 MSqlQuery: SELECT data FROM settings WHERE value = 'MasterServerPort' AND hostname IS NULL;
2008-04-04 00:23:16.196 MythSocket(78bd70:4): new socket
2008-04-04 00:23:16.196 MSqlQuery: SELECT data FROM settings WHERE value = 'WOLbackendReconnectWaitTime' AND hostname = 'mythbox' ;
2008-04-04 00:23:16.196 MSqlQuery: SELECT data FROM settings WHERE value = 'WOLbackendReconnectWaitTime' AND hostname IS NULL;
2008-04-04 00:23:16.197 MSqlQuery: SELECT data FROM settings WHERE value = 'WOLbackendConnectRetry' AND hostname = 'mythbox' ;
2008-04-04 00:23:16.197 MSqlQuery: SELECT data FROM settings WHERE value = 'WOLbackendConnectRetry' AND hostname IS NULL;
2008-04-04 00:23:16.197 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-04-04 00:23:16.197 MythSocket(78c9f0:5): new socket
2008-04-04 00:23:16.197 MythSocket(78c9f0:5): attempting connect() to (127.0.0.1:6543)
2008-04-04 00:23:16.197 MythSocket(78c9f0:5): state change Idle -> Connected
2008-04-04 00:23:16.197 write ->  5 21      MYTH_PROTO_VERSION 40
2008-04-04 00:23:16.231 read  <-  5 13      ACCEPT[]:[]40
2008-04-04 00:23:16.231 Using protocol version 40
2008-04-04 00:23:16.231 write ->  5 21      ANN Monitor mythbox 0
2008-04-04 00:23:16.262 read  <-  5 2       OK
2008-04-04 00:23:16.262 MythSocket(78bd70:4): attempting connect() to (127.0.0.1:6543)
2008-04-04 00:23:16.262 MythSocket(78bd70:4): state change Idle -> Connected
2008-04-04 00:23:16.262 write ->  4 21      ANN Monitor mythbox 1
2008-04-04 00:23:16.275 read  <-  4 2       OK
2008-04-04 00:23:16.276 MythSocket: readyread thread start
2008-04-04 00:23:16.276 MythSocket(78bd70:4): UpRef: 1
2008-04-04 00:23:16.290 MSqlQuery: SELECT data FROM settings WHERE value = 'LCDServerPort' AND hostname = 'mythbox' ;
2008-04-04 00:23:16.290 MSqlQuery: SELECT data FROM settings WHERE value = 'LCDServerPort' AND hostname IS NULL;
2008-04-04 00:23:16.306 MSqlQuery: SELECT data FROM settings WHERE value = 'LCDHost' AND hostname = 'mythbox' ;
2008-04-04 00:23:16.306 MSqlQuery: SELECT data FROM settings WHERE value = 'LCDHost' AND hostname IS NULL;
2008-04-04 00:23:16.307 MSqlQuery: SELECT data FROM settings WHERE value = 'LCDPort' AND hostname = 'mythbox' ;
2008-04-04 00:23:16.307 MSqlQuery: SELECT data FROM settings WHERE value = 'LCDPort' AND hostname IS NULL;
2008-04-04 00:23:16.322 MSqlQuery: SELECT data FROM settings WHERE value = 'LCDEnable' AND hostname = 'mythbox' ;
2008-04-04 00:23:16.425 MSqlQuery: SELECT data FROM settings WHERE value = 'LCDBigClock' AND hostname = 'mythbox' ;
2008-04-04 00:23:16.447 MSqlQuery: SELECT data FROM settings WHERE value = 'TimeFormat' AND hostname = 'mythbox' ;
2008-04-04 00:23:16.448 MSqlQuery: SELECT data FROM settings WHERE value = 'LCDShowMusic' AND hostname = 'mythbox' ;
2008-04-04 00:23:16.448 MSqlQuery: SELECT data FROM settings WHERE value = 'LCDShowMusicItems' AND hostname = 'mythbox' ;
2008-04-04 00:23:16.449 MSqlQuery: SELECT data FROM settings WHERE value = 'LCDShowTime' AND hostname = 'mythbox' ;
2008-04-04 00:23:16.449 MSqlQuery: SELECT data FROM settings WHERE value = 'LCDShowChannel' AND hostname = 'mythbox' ;
2008-04-04 00:23:16.450 MSqlQuery: SELECT data FROM settings WHERE value = 'LCDShowGeneric' AND hostname = 'mythbox' ;
2008-04-04 00:23:16.450 MSqlQuery: SELECT data FROM settings WHERE value = 'LCDShowVolume' AND hostname = 'mythbox' ;
2008-04-04 00:23:16.451 MSqlQuery: SELECT data FROM settings WHERE value = 'LCDShowMenu' AND hostname = 'mythbox' ;
2008-04-04 00:23:16.452 MSqlQuery: SELECT data FROM settings WHERE value = 'LCDShowRecStatus' AND hostname = 'mythbox' ;
2008-04-04 00:23:16.452 MSqlQuery: SELECT data FROM settings WHERE value = 'LCDBacklightOn' AND hostname = 'mythbox' ;
2008-04-04 00:23:16.453 MSqlQuery: SELECT data FROM settings WHERE value = 'LCDHeartBeatOn' AND hostname = 'mythbox' ;
2008-04-04 00:23:16.453 MSqlQuery: SELECT data FROM settings WHERE value = 'LCDPopupTime' AND hostname = 'mythbox' ;
2008-04-04 00:23:16.454 MSqlQuery: SELECT data FROM settings WHERE value = 'LCDKeyString' AND hostname = 'mythbox' ;
2008-04-04 00:23:16.480 MSqlQuery: SELECT cardid FROM capturecard ORDER BY cardid
2008-04-04 00:23:16.481 write ->  5 35      QUERY_REMOTEENCODER 1[]:[]GET_STATE
2008-04-04 00:23:16.481 read  <-  5 1       4
2008-04-04 00:23:16.481 write ->  5 34      QUERY_RECORDER 1[]:[]GET_RECORDING
2008-04-04 00:23:16.522 read  <-  5 510     Late Night With Conan O'Brien[]:[][]:[]Olympic athlete Bode Miller; Cobra Starship performs.[]:[]Talk[]:[]3021[]:[]2-1[]:[]KPRC-HD[]:$
2008-04-04 00:23:16.522 write ->  5 35      QUERY_REMOTEENCODER 2[]:[]GET_STATE
2008-04-04 00:23:16.522 read  <-  5 1       0
2008-04-04 00:23:16.522 write ->  5 35      QUERY_REMOTEENCODER 3[]:[]GET_STATE
2008-04-04 00:23:16.527 read  <-  5 2       -1
2008-04-04 00:23:16.528 LCDProcClient: WARNING: Something is gettingpassed to LCDd that it doesn't understand
2008-04-04 00:23:16.528 last command: widget_set Time timeWidget 5 2 "12 23 AM"

```

---

### Post by ian dobson on 2008-04-04
Hi,

Have a look here: [http://www.mythtv.org/wiki/index.php/Mythlcdserver](http://www.mythtv.org/wiki/index.php/Mythlcdserver)

Looks as if the protocol versions for Mythlcd and lcdproc don't match. That could be your problem, but I'm not sure how to fix it, maybe compile a new version of lcdproc.

Regards
Ian Dobson

---

### Post by superm1 on 2008-04-04
When you guys identify the proper problem/solution, please file a bug about it soon to the appropriate source package.

---

### Post by whoisvince on 2008-04-04
I'm running MythTV 0.21 with LCDProc 0.5.2, so there shouldn't be any conflict.  MythTV 0.20 ran OK with LCDProc 0.5.2.

I'll step down the LCDProc version and report back.

---

### Post by whoisvince on 2008-04-04
Hardy only supplies lcdproc 0.5.2 with the distro, so I compiled lcdproc 0.5.1 and lcdproc 0.5.0 and tried them both, but the CPU use for mythlcdserver remained excessive and I'm getting the same error in the logfile about commands getting passed to LCDd that it doesn't understand.

I also got this error from LCDd:
```
-error: huh? Usage: client_add_key [-exclusively|-shared] {<key>}+
```

Is anyone else having the CPU use problem?

---

