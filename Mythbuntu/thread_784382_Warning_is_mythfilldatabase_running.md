---
title: "Warning is mythfilldatabase running?"
date: 2008-05-06
forum: Mythbuntu
---

### Post by mtbdrew on 2008-05-06
First off let me say I'm to Mythbuntu.

Anyway, I'm trying to setup a frontend/backend using the latest 8.04 cd on:
ECS K7S5A Pro (Sis chipset) with AMD XP2000+
FX5500
AverTVHD MCE A180
Seagate 300GB IDE
1Gig Mem

The installation goes fine and I have installed the firmware for the tuner card.
Run setup for both front and back ends left everything at default except IP addresses.
Managed to get the tuner card to scan for local over the air channels. 
Setup storage dir.
Logged out and mythfilldatabase runs.
Reset system and it comes up with the front end running. However when I go to watch live TV the screen goes blank for a couple of seconds then comes back to menu options.
Status window shows following:
Warning: is mythfilldatabase running?
I can go to on screen guide and schedule a recording but when it tries to start to record I get message:
Could not connect to back end.

I've loaded MythDora 5 and everything works so I know it's not a hardware issue.
Any ideas?

Thanks
Andrew

---

### Post by mtbdrew on 2008-05-07
Anybody??

---

### Post by amphibem on 2008-05-07
Well I will have a stab as I had this problem at some stage, not certain of this is the solution though..

In the backend setup make sure you setup an video source; and then make sure both the tuner and all your channels are linked to this source.

---

### Post by mtbdrew on 2008-05-08
> **amphibem said:**
> Well I will have a stab as I had this problem at some stage, not certain of this is the solution though..

In the backend setup make sure you setup an video source; and then make sure both the tuner and all your channels are linked to this source.

Thanks for the reply amphibem, unfortunately I have already tried that several times. I am able to scan and detect local channels fine and if I go into the program guide I can see programs and setup a record time but when the box goes to record I get a could not connect to backend error.

I installed MythDora 5 last night and everything worked out of the box. Didn't have to do the firmware patch as it was all already included in the build. I've used Ubuntu in that past so would rather get Mythbuntu working but this is craziness:confused:

---

### Post by mtbdrew on 2008-05-09
Well the responses were so overwhelming, not!

I guess I'll just have to stick with MythDora 5 as it works out of the box.

---

### Post by tech9 on 2008-05-09
> **mtbdrew said:**
> Well the responses were so overwhelming, not!

I guess I'll just have to stick with MythDora 5 as it works out of the box.

try to restart the mythbackend

---

### Post by mtbdrew on 2008-05-15
> **tech9 said:**
> try to restart the mythbackend


Thanks for the suggestion but I tried that and still no help.

---

### Post by mtbdrew on 2008-05-20
Here is the printout:

mythbox@mythtv:~$ mythtv /etc/init.d/mythtv-backend start
2008-05-20 22:48:29.735 Using runtime prefix = /usr, libdir = /usr/lib
2008-05-20 22:48:29.744 XScreenSaver support enabled
2008-05-20 22:48:29.753 DPMS is active.
2008-05-20 22:48:29.754 Empty LocalHostName.
2008-05-20 22:48:29.754 Using localhost value of mythtv
2008-05-20 22:48:29.796 New DB connection, total: 1
2008-05-20 22:48:29.802 Connected to database 'mythconverg' at host: 192.168.101.179
2008-05-20 22:48:29.803 Closing DB connection named 'DBManager0'
2008-05-20 22:48:29.805 Primary screen 0.
2008-05-20 22:48:29.806 Connected to database 'mythconverg' at host: 192.168.101.179
2008-05-20 22:48:29.808 Using screen 0, 1280x1024 at 0,0
2008-05-20 22:48:29.864 max_width: 1280 max_height: 1024
2008-05-20 22:48:29.866 Primary screen 0.
2008-05-20 22:48:29.867 Using screen 0, 1280x1024 at 0,0
2008-05-20 22:48:29.870 Switching to square mode (blue)
2008-05-20 22:48:29.926 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2008-05-20 22:48:29.927 lirc_init failed for mythtv, see preceding messages
2008-05-20 22:48:29.927 JoystickMenuClient Error: Joystick disabled - Failed to read /home/mythbox/.mythtv/joystickmenurc
2008-05-20 22:48:30.907 New DB connection, total: 2
2008-05-20 22:48:30.908 Connected to database 'mythconverg' at host: 192.168.101.179
2008-05-20 22:48:30.968 Connecting to backend server: 192.168.101.179:6543 (try 1 of 5)
2008-05-20 22:48:30.969 Using protocol version 40
2008-05-20 22:48:30.983 TV: Attempting to change from None to WatchingPreRecorded
2008-05-20 22:48:30.998 RingBuf(/home/mythbox/start): OpenFile(/home/mythbox/start, 12)
2008-05-20 22:48:37.499 RingBuf(/home/mythbox/start): Could not open /home/mythbox/start.
2008-05-20 22:48:37.499 RingBuf(/home/mythbox/start): CalcReadAheadThresh(3085941840 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
Mutex destroy failure: Device or resource busy
mythbox@mythtv:~$ mythtv /etc/init.d/mythtv-backend restart
2008-05-20 22:49:18.096 Using runtime prefix = /usr, libdir = /usr/lib
2008-05-20 22:49:18.106 XScreenSaver support enabled
2008-05-20 22:49:18.113 DPMS is active.
2008-05-20 22:49:18.114 Empty LocalHostName.
2008-05-20 22:49:18.114 Using localhost value of mythtv
2008-05-20 22:49:18.149 New DB connection, total: 1
2008-05-20 22:49:18.154 Connected to database 'mythconverg' at host: 192.168.101.179
2008-05-20 22:49:18.155 Closing DB connection named 'DBManager0'
2008-05-20 22:49:18.157 Primary screen 0.
2008-05-20 22:49:18.158 Connected to database 'mythconverg' at host: 192.168.101.179
2008-05-20 22:49:18.159 Using screen 0, 1280x1024 at 0,0
2008-05-20 22:49:18.210 max_width: 1280 max_height: 1024
2008-05-20 22:49:18.236 Primary screen 0.
2008-05-20 22:49:18.237 Using screen 0, 1280x1024 at 0,0
2008-05-20 22:49:18.239 Switching to square mode (blue)
2008-05-20 22:49:18.298 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2008-05-20 22:49:18.299 lirc_init failed for mythtv, see preceding messages
2008-05-20 22:49:18.300 JoystickMenuClient Error: Joystick disabled - Failed to read /home/mythbox/.mythtv/joystickmenurc
2008-05-20 22:49:19.238 New DB connection, total: 2
2008-05-20 22:49:19.239 Connected to database 'mythconverg' at host: 192.168.101.179
2008-05-20 22:49:19.294 Connecting to backend server: 192.168.101.179:6543 (try 1 of 5)
2008-05-20 22:49:19.295 Using protocol version 40
2008-05-20 22:49:19.301 TV: Attempting to change from None to WatchingPreRecorded
2008-05-20 22:49:19.302 RingBuf(/home/mythbox/restart): OpenFile(/home/mythbox/restart, 12)
2008-05-20 22:49:25.802 RingBuf(/home/mythbox/restart): Could not open /home/mythbox/restart.
2008-05-20 22:49:25.802 RingBuf(/home/mythbox/restart): CalcReadAheadThresh(3086715984 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
Mutex destroy failure: Device or resource busy

---

### Post by mtbdrew on 2008-05-21
Somebody, anybody?

---

### Post by mtbdrew on 2008-05-21
Figured it out - needed to set the permissions on the record directories to allow mythtv access.

---

### Post by mrand on 2008-05-21
> **mtbdrew said:**
> <...>
2008-05-20 22:49:18.158 Connected to database 'mythconverg' at host: 192.168.101.179
2008-05-20 22:49:18.159 Using screen 0, 1280x1024 at 0,0
2008-05-20 22:49:18.210 max_width: 1280 max_height: 1024
2008-05-20 22:49:18.236 Primary screen 0.
2008-05-20 22:49:18.237 Using screen 0, 1280x1024 at 0,0
2008-05-20 22:49:18.239 Switching to square mode (blue)
2008-05-20 22:49:18.298 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2008-05-20 22:49:18.299 lirc_init failed for mythtv, see preceding messages
2008-05-20 22:49:18.300 JoystickMenuClient Error: Joystick disabled - Failed to read /home/mythbox/.mythtv/joystickmenurc
2008-05-20 22:49:19.238 New DB connection, total: 2
2008-05-20 22:49:19.239 Connected to database 'mythconverg' at host: 192.168.101.179
2008-05-20 22:49:19.294 Connecting to backend server: 192.168.101.179:6543 (try 1 of 5)
2008-05-20 22:49:19.295 Using protocol version 40
2008-05-20 22:49:19.301 TV: Attempting to change from None to WatchingPreRecorded
2008-05-20 22:49:19.302 RingBuf(/home/mythbox/restart): OpenFile(/home/mythbox/restart, 12)
2008-05-20 22:49:25.802 RingBuf(/home/mythbox/restart): Could not open /home/mythbox/restart.
2008-05-20 22:49:25.802 RingBuf(/home/mythbox/restart): CalcReadAheadThresh(3086715984 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
Mutex destroy failure: Device or resource busyThere are several errors in your log which seem to indicate errors opening files (ringbuf, lirc, and joystick are all complaining).  Have you verified the above paths are correct and/or exist?  Is this a completely stock mythtv install, or are you trying to change the paths?  /var/lib/mythtv is the normal path for the recordings.

Good luck.

[INDENT]   Marc[/INDENT]

---

