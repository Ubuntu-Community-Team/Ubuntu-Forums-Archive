---
title: "mythbackend issues"
date: 2008-04-08
forum: Mythbuntu
---

### Post by Naegling23 on 2008-04-08
I recently upgraded my mythtv package.

Before everything worked fine, mythtv is set to start on boot with the command mythbackend & mythfrontend.

however, now the frontend does not connect to the backend.  In order to get it to work, I have to exit out, kill mythbackend, and restart it.  Then everything works fine again....so how do I fix this problem?  I want mythbackend working on boot!!!

---

### Post by vancheese on 2008-04-09
Phew, I'm having the same issue, from a mythbuntu install and was wondering if I was a complete muppet

---

### Post by laga on 2008-04-09
See the link in my signature to find out how to provide log files.

---

### Post by Naegling23 on 2008-04-13
here is the mythbackend log file
2008-04-13 16:18:16.809 Using runtime prefix = /usr, libdir = /usr/lib
2008-04-13 16:18:17.173 Empty LocalHostName.
2008-04-13 16:18:17.397 Using localhost value of twasbrillg-desktop
2008-04-13 16:18:18.272 New DB connection, total: 1
2008-04-13 16:18:18.485 Connected to database 'mythconverg' at host: localhost
2008-04-13 16:18:18.632 Closing DB connection named 'DBManager0'
2008-04-13 16:18:18.745 Connected to database 'mythconverg' at host: localhost
2008-04-13 16:18:19.008 New DB connection, total: 2
2008-04-13 16:18:19.197 Connected to database 'mythconverg' at host: localhost
2008-04-13 16:18:19.679 Current Schema Version: 1214
Starting up as the master server.
2008-04-13 16:18:19.765 New DB connection, total: 3
2008-04-13 16:18:19.974 Connected to database 'mythconverg' at host: localhost
2008-04-13 16:18:20.407 New DB scheduler connection
2008-04-13 16:18:20.642 Connected to database 'mythconverg' at host: localhost
2008-04-13 16:18:22.462 Main::Registering HttpStatus Extension
2008-04-13 16:18:22.834 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-04-13 16:18:22.836 Enabled verbose msgs:  important general
2008-04-13 16:18:22.845 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-04-13 16:18:22.850 SG(Default) Error: Group 'Default' wants to use directory '/home/twasbrillg', but this directory is not writeable.
2008-04-13 16:18:24.253 Reschedule requested for id -1.
2008-04-13 16:18:24.768 Scheduled 6 items in 0.5 = 0.17 match + 0.34 place
2008-04-13 16:18:24.799 Seem to be woken up by USER
2008-04-13 16:18:31.346 UPnpMedia: BuildMediaMap VIDEO scan starting in :/home/twasbrillg/Videos:
2008-04-13 16:18:32.805 UPnpMedia: BuildMediaMap Done. Found 235 objects

---

### Post by Naegling23 on 2008-04-13
this is from the mythbackend log1 file, I think it might hold more information
2008-04-13 13:33:08.380 Connecting to backend server: 192.168.1.101:6543 (try 1 of 5)
2008-04-13 13:33:08.442 Using protocol version 40
2008-04-13 13:33:08.445 MainServer::HandleAnnounce Monitor
2008-04-13 13:33:08.448 adding: twasbrillg-desktop as a client (events: 0)
2008-04-13 13:33:08.450 MainServer::HandleAnnounce Monitor
2008-04-13 13:33:08.452 adding: twasbrillg-desktop as a client (events: 1)
2008-04-13 13:33:08.508 Reschedule requested for id -1.
2008-04-13 13:33:08.530 Received a remote 'Clear Cache' request
2008-04-13 13:33:08.531 mythfilldatabase run complete.
2008-04-13 13:33:08.532 MythSocket(824ebf0:-1): writeStringList: Error, socket went unconnected.
2008-04-13 13:33:08.700 Scheduled 6 items in 0.2 = 0.06 match + 0.13 place
Segmentation fault (core dumped)
2008-04-13 13:33:27.554 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-04-13 13:34:55.624 MainServer::HandleAnnounce Monitor
2008-04-13 13:34:55.629 adding: twasbrillg-desktop as a client (events: 0)
2008-04-13 13:34:55.630 MainServer::HandleAnnounce Monitor
2008-04-13 13:34:55.632 adding: twasbrillg-desktop as a client (events: 1)
2008-04-13 13:34:55.682 MainServer::HandleAnnounce Playback
2008-04-13 13:34:55.701 adding: twasbrillg-desktop as a client (events: 0)
2008-04-13 13:34:55.735 TVRec(1): Changing from None to WatchingLiveTV
2008-04-13 13:34:55.797 TVRec(1): HW Tuner: 1->1
2008-04-13 13:34:55.969 SampleRate: Attempted to add a rate 32000 Hz, which is not in the list of allowed rates.
2008-04-13 13:34:57.185 TFW, Error: Opening file '/home/twasbrillg/1049_20080413133456.nuv'.
			eno: Permission denied (13)
2008-04-13 13:34:57.189 TVRec(1) Error: RingBuffer '/home/twasbrillg/1049_20080413133456.nuv' not open...
2008-04-13 13:34:57.190 TVRec(1) Error: CreateLiveTVRingBuffer() failed
2008-04-13 13:34:57.192 TVRec(1) Error: Failed to create RingBuffer 2
2008-04-13 13:34:57.195 TVRec(1): Changing from WatchingLiveTV to None
2008-04-13 13:34:57.197 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

---

### Post by volkswagner on 2008-04-13
I had the same problem, both in .20 and .21.  I made all my machines static ip's via network manager.  Uncheck allow roam mode and enter your LAN info.

---

### Post by Naegling23 on 2008-04-13
is that what this error is saying?

the ip was already set to static.

---

### Post by volkswagner on 2008-04-13
Sorry, no.  The symptoms and solutions were the same as mine.

I see these errors:

2008-04-13 13:34:55.797 TVRec(1): HW Tuner: 1->1
2008-04-13 13:34:55.969 SampleRate: Attempted to add a rate 32000 Hz, which is not in the list of allowed rates.
2008-04-13 13:34:57.185 TFW, Error: Opening file '/home/twasbrillg/1049_20080413133456.nuv'.
eno: Permission denied (13)
2008-04-13 13:34:57.189 TVRec(1) Error: RingBuffer '/home/twasbrillg/1049_20080413133456.nuv' not open...
2008-04-13 13:34:57.190 TVRec(1) Error: CreateLiveTVRingBuffer() failed
2008-04-13 13:34:57.192 TVRec(1) Error: Failed to create RingBuffer 2

Not sure what the sample rate issue is (sound config?).  Have you checked the permissions for /home/wasbrillg?

```
ls -alt /home/wasbrillg
```

Here is the thread I started when my backend did not start on boot.  It has some useful commands to see what the backend is doing.

---

### Post by Naegling23 on 2008-04-21
ok, so I fixed the problem, but not in a good way.  I chmod 777'd my entire home folder.  This fixed the problem.  I guess I was having permission problems related to some of the files.  Since I was using sudo to kill the backend, I was logging back in as sudo in the terminal, and I never noticed that it was a permission problem.....But now everyone has full permissions on my home folder!!!  So, what is the best way to fix this?  Is there a setting in mythtv that can set users?  Should I just chmod 775?

---

