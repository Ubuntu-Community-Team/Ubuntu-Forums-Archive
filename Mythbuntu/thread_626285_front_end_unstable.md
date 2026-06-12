---
title: "front end unstable"
date: 2007-11-28
forum: Mythbuntu
---

### Post by aspenelm on 2007-11-28
Hello, just installed mythbuntu 7.10.  Mythbuntu on the backend is good so far, I am able to get tv listings and record ATSC shows.  The frontend (on a different machine) I am having some issues.  I can play some prerecorded shows without problems including HD shows, other times it segfaults, it seems random at this point but I haven't done any testing to see if it is repeatable.  Thought maybe someone here could point me in the right direction.

Note:  The frontend is Kubuntu 7.10 with the mythtv frontend installed.  I did have to use the drivers downloaded from nvidia instead of the ubuntu restricted driver, this fixed some video playback issues.  

Backend
DIY Tower, Athlon XP @ 2.5Ghz
Nforce2 Chipset
1 GB memory, 1 GB swap, 100 GB recordings storage 
pchdtv 5500 tuner 
Nvidia Geforce 5500 graphics

Frontend:
Dell 9300 Laptop, Pentium M @ 2 GHz, 
Intel Centrino, 
2 GB memory, 1GB swap, 
Geforce Go 6800 Graphics


Below is output from mythfrontend prior to a segfault, is there anything obviously wrong. Video? Do I need to do anything with the realtime priority?, sleep with busy waits doesn't sound right.  I watched one recording full screen, fast forwarded through sections of it, then went back to the "manage recordings screen" in mythtv, scrolled through the prerecorded videos, then it crashed.

Mythfrontend output on command line preceding segfault:
```
mythfrontend
2007-11-28 22:00:28.690 Using runtime prefix = /usr
2007-11-28 22:00:28.692 DPMS is disabled.
2007-11-28 22:00:28.702 New DB connection, total: 1
2007-11-28 22:00:38.732 Connected to database 'mythconverg' at host: 192.168.2.5
2007-11-28 22:00:38.733 Total desktop dim: 1920x1200, with 1 screen[s].
2007-11-28 22:00:38.735 Using screen 0, 1920x1200 at 0,0
2007-11-28 22:00:38.780 Current Schema Version: 1160
2007-11-28 22:00:38.790 mythfrontend version: 0.20.20070821-1 www.mythtv.org
2007-11-28 22:00:38.790 Enabled verbose msgs:  important general
2007-11-28 22:00:39.012 Total desktop dim: 1920x1200, with 1 screen[s].
2007-11-28 22:00:39.013 Using screen 0, 1920x1200 at 0,0
2007-11-28 22:00:39.014 Switching to square mode (blue)
2007-11-28 22:00:39.028 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2007-11-28 22:00:39.484 Joystick disabled.
2007-11-28 22:00:39.806 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-11-28 22:00:40.258 Registering Internal as a media playback plugin.
2007-11-28 22:00:46.099 XMLParse::LoadTheme using /usr/share/mythtv/themes/blue/ui.xml
2007-11-28 22:00:46.518 Connecting to backend server: 192.168.2.5:6543 (try 1 of 5)
2007-11-28 22:00:46.519 Using protocol version 31
0: start_time: 5145.652 duration: 323.701
1: start_time: 5145.616 duration: 323.698
stream: start_time: 57173.508 duration: 3597.085 bitrate=13532 kb/s
2007-11-28 22:00:47.634 AFD: Opened codec 0x92bdb20, id(MPEG2VIDEO) type(Video)
2007-11-28 22:00:47.635 AFD: Opened codec 0x92bd730, id(AC3) type(Audio)
0: start_time: 5145.652 duration: 323.701
1: start_time: 5145.616 duration: 323.698
stream: start_time: 57173.508 duration: 3597.085 bitrate=13532 kb/s
2007-11-28 22:00:48.645 AFD: Opened codec 0x92bc620, id(MPEG2VIDEO) type(Video)
2007-11-28 22:00:48.646 AFD: Opened codec 0x925bf50, id(AC3) type(Audio)
0: start_time: 4821.642 duration: 323.692
1: start_time: 4821.603 duration: 323.696
stream: start_time: 53573.363 duration: 3597.016 bitrate=11830 kb/s
2007-11-28 22:00:49.414 AFD: Opened codec 0x9390ac0, id(MPEG2VIDEO) type(Video)
2007-11-28 22:00:49.415 AFD: Opened codec 0x9390e10, id(AC3) type(Audio)
2007-11-28 22:00:52.062 New DB connection, total: 2
2007-11-28 22:01:02.067 Connected to database 'mythconverg' at host: 192.168.2.5
2007-11-28 22:01:02.101 TV: Attempting to change from None to WatchingPreRecorded
0: start_time: 4821.642 duration: 323.692
1: start_time: 4821.603 duration: 323.696
stream: start_time: 53573.363 duration: 3597.016 bitrate=11830 kb/s
2007-11-28 22:01:02.150 AFD: Opened codec 0x83e57b0, id(MPEG2VIDEO) type(Video)
2007-11-28 22:01:02.151 AFD: Opened codec 0x83e5db0, id(AC3) type(Audio)
2007-11-28 22:01:02.156 Opening ALSA audio device 'default'.
2007-11-28 22:01:02.379 VideoOutputXv: XvMCTex: Init failed
2007-11-28 22:01:02.379 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  141
  Minor opcode:  14
  Resource id:  0x20c
2007-11-28 22:01:02.923 TV: Changing from None to WatchingPreRecorded
2007-11-28 22:01:02.986 Realtime priority would require SUID as root.
2007-11-28 22:01:03.116 Video timing method: USleep with busy wait
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 3 29
[mpeg2video @ 0xb7321ce8]mb incr damaged
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 1 31
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 7 32
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 44 33
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 9 34
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 21 35
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 16 36
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 6 37
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 20 38
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 31 39
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 3 40
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 13 41
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 36 42
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 28 43
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 1 44
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 49 30
[mpeg2video @ 0xb7321ce8]invalid cbp at 9 31
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 45 32
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 26 33
[mpeg2video @ 0xb7321ce8]invalid cbp at 2 34
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 21 35
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 2 36
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 67 37
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 1 38
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 39
[mpeg2video @ 0xb7321ce8]slice mismatch
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 27 41
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 1 42
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 1 43
[mpeg2video @ 0xb7321ce8]end mismatch left=2959 145F0C
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 27 1
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 5 2
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 17 3
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 1 4
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 7 5
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 10 6
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 1 7
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 2 8
[mpeg2video @ 0xb7321ce8]mb incr damaged
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 29 10
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 24 11
[mpeg2video @ 0xb7321ce8]invalid cbp at 8 12
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 51 13
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 4 14
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 9 15
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 33 16
[mpeg2video @ 0xb7321ce8]slice mismatch
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 7 18
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 23 19
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 4 20
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 10 21
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 39 22
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 7 24
[mpeg2video @ 0xb7321ce8]mb incr damaged
[mpeg2video @ 0xb7321ce8]mb incr damaged
[mpeg2video @ 0xb7321ce8]slice mismatch
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 6 27
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 9 28
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 14 29
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 38 30
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 9 31
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 1 32
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 4 33
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 1 34
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 22 35
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 26 36
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 2 37
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 4 38
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 39
[mpeg2video @ 0xb7321ce8]invalid cbp at 25 40
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 15 41
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 3 42
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 16 43
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 5 44
2007-11-28 22:10:53.032 NVP: prebuffering pause
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 40 27
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 14 28
[mpeg2video @ 0xb7321ce8]mb incr damaged
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 4 30
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 29 31
[mpeg2video @ 0xb7321ce8]mb incr damaged
[mpeg2video @ 0xb7321ce8]mb incr damaged
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 29 34
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 4 35
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 28 37
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 25 37
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 6 38
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 1 39
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 32 40
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 41
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 42
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 43
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 44
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 1 43
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 1 44
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 9 37
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 33 38
[mpeg2video @ 0xb7321ce8]mb incr damaged
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 12 40
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 71 41
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 5 42
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 3 43
[mpeg2video @ 0xb7321ce8]end mismatch left=2307 2AEFF7
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 3 25
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 26
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 3 27
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 50 28
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 10 29
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 7 30
[mpeg2video @ 0xb7321ce8]invalid cbp at 4 31
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 6 32
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 3 33
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 9 34
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 17 35
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 47 36
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 5 37
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 5 38
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 8 39
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 35 40
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 4 41
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 11 42
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 3 43
[mpeg2video @ 0xb7321ce8]invalid cbp at 33 44
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 30 42
[mpeg2video @ 0xb7321ce8]invalid cbp at 11 43
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 1 44
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 75 7
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 61 8
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 66 9
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 6 10
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 30 11
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 2 12
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 17 13
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 3 14
[mpeg2video @ 0xb7321ce8]invalid cbp at 57 15
[mpeg2video @ 0xb7321ce8]mb incr damaged
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 23 17
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 27 18
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 51 19
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 46 20
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 23 21
[mpeg2video @ 0xb7321ce8]invalid cbp at 21 22
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 15 23
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 8 24
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 14 26
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 39 26
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 16 27
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 9 29
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 24 29
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 57 30
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 23 31
[mpeg2video @ 0xb7321ce8]slice mismatch
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 63 33
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 34
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 51 36
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 3 36
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 5 37
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 12 38
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 39
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 2 40
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 4 42
[mpeg2video @ 0xb7321ce8]invalid cbp at 62 42
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 8 43
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 52 44
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 4 16
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 17
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 18
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 1 19
[mpeg2video @ 0xb7321ce8]invalid cbp at 4 20
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 21 21
[mpeg2video @ 0xb7321ce8]mb incr damaged
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 4 23
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 17 24
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 24 25
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 18 26
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 1 27
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 28
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 6 29
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 1 30
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 78 31
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 25 32
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 1 33
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 49 34
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 10 35
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 9 36
[mpeg2video @ 0xb7321ce8]mb incr damaged
[mpeg2video @ 0xb7321ce8]mb incr damaged
[mpeg2video @ 0xb7321ce8]mb incr damaged
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 7 40
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 48 41
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 8 42
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 48 43
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 6 44
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 17 30
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 58 31
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 39 32
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 33
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 13 34
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 35
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 45 36
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 3 37
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 38
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 26 39
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 33 40
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 21 41
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 24 42
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 33 43
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 44
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 21 21
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 1 22
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 23
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 1 24
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 2 25
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 27 26
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 15 27
[mpeg2video @ 0xb7321ce8]mb incr damaged
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 11 29
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 30
[mpeg2video @ 0xb7321ce8]slice mismatch
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 65 32
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 11 33
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 2 34
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 2 35
[mpeg2video @ 0xb7321ce8]mb incr damaged
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 29 38
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 9 38
[mpeg2video @ 0xb7321ce8]invalid cbp at 3 39
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 17 40
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 41
[mpeg2video @ 0xb7321ce8]mb incr damaged
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 54 43
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 6 44
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 69 1
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 14 2
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 1 3
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 7 4
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 11 5
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 15 6
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 14 7
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 2 8
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 14 9
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 2 10
[mpeg2video @ 0xb7321ce8]mb incr damaged
[mpeg2video @ 0xb7321ce8]mb incr damaged
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 11 13
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 16 14
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 14 15
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 34 16
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 1 17
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 36 18
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 21 19
[mpeg2video @ 0xb7321ce8]slice mismatch
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 12 21
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 10 22
[mpeg2video @ 0xb7321ce8]mb incr damaged
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 6 24
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 3 25
[mpeg2video @ 0xb7321ce8]mb incr damaged
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 27
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 2 28
[mpeg2video @ 0xb7321ce8]slice mismatch
[mpeg2video @ 0xb7321ce8]slice mismatch
[mpeg2video @ 0xb7321ce8]invalid cbp at 39 31
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 3 32
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 13 33
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 3 34
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 1 35
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 36
[mpeg2video @ 0xb7321ce8]mb incr damaged
[mpeg2video @ 0xb7321ce8]invalid cbp at 15 38
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 53 39
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 1 40
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 8 41
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 2 42
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 24 43
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 48 44
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 58 1
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 2 2
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 1 3
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 7 4
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 6 5
[mpeg2video @ 0xb7321ce8]mb incr damaged
[mpeg2video @ 0xb7321ce8]mb incr damaged
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 16 8
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 9 9
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 20 10
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 11
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 11 12
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 29 13
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 7 14
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 12 15
[mpeg2video @ 0xb7321ce8]invalid cbp at 25 16
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 17
[mpeg2video @ 0xb7321ce8]slice mismatch
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 14 19
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 18 20
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 21 21
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 10 22
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 39 23
[mpeg2video @ 0xb7321ce8]invalid cbp at 24 24
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 1 25
[mpeg2video @ 0xb7321ce8]invalid cbp at 1 26
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 1 27
[mpeg2video @ 0xb7321ce8]mb incr damaged
[mpeg2video @ 0xb7321ce8]invalid cbp at 44 29
[mpeg2video @ 0xb7321ce8]mb incr damaged
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 5 31
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 10 32
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 11 33
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 3 34
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 16 35
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 13 36
[mpeg2video @ 0xb7321ce8]invalid cbp at 38 37
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 7 38
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 8 39
[mpeg2video @ 0xb7321ce8]slice mismatch
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 3 41
[mpeg2video @ 0xb7321ce8]slice mismatch
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 32 43
[mpeg2video @ 0xb7321ce8]mb incr damaged
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 16 38
[mpeg2video @ 0xb7321ce8]mb incr damaged
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 1 40
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 30 41
[mpeg2video @ 0xb7321ce8]mb incr damaged
[mpeg2video @ 0xb7321ce8]mb incr damaged
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 1 44
[mpeg2video @ 0xb7321ce8]invalid cbp at 9 23
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 7 24
[mpeg2video @ 0xb7321ce8]mb incr damaged
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 9 26
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 21 27
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 4 28
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 2 29
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 14 30
[mpeg2video @ 0xb7321ce8]mb incr damaged
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 32
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 3 33
[mpeg2video @ 0xb7321ce8]mb incr damaged
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 1 35
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 36
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 16 37
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 3 38
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 2 39
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 20 40
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 5 41
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 2 42
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 1 43
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 2 44
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 34
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 35
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 36
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 37
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 38
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 39
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 40
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 41
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 42
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 43
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 44
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 1 13
[mpeg2video @ 0xb7321ce8]invalid cbp at 65 14
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 15
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 4 16
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 17
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 23 18
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 7 19
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 10 20
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 3 21
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 2 22
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 9 23
[mpeg2video @ 0xb7321ce8]invalid cbp at 4 24
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 2 25
[mpeg2video @ 0xb7321ce8]mb incr damaged
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 55 27
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 20 28
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 1 29
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 30
[mpeg2video @ 0xb7321ce8]mb incr damaged
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 7 32
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 3 33
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 1 34
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 1 35
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 3 36
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 1 37
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 9 38
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 39
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 35 40
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 3 41
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 4 42
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 7 43
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 44
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 20 33
[mpeg2video @ 0xb7321ce8]slice mismatch
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 36
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 1 36
[mpeg2video @ 0xb7321ce8]mb incr damaged
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 38
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 15 39
[mpeg2video @ 0xb7321ce8]mb incr damaged
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 73 41
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 15 42
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 27 43
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 5 44
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 1 27
[mpeg2video @ 0xb7321ce8]invalid cbp at 1 28
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 1 29
[mpeg2video @ 0xb7321ce8]slice mismatch
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 31
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 47 32
[mpeg2video @ 0xb7321ce8]mb incr damaged
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 34
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 21 35
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 34 36
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 37
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 38
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 39
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 40
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 41
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 42
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 43
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 44
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 3 20
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 3 21
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 22
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 13 23
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 18 24
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 25
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 2 26
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 10 27
[mpeg2video @ 0xb7321ce8]mb incr damaged
[mpeg2video @ 0xb7321ce8]mb incr damaged
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 2 30
[mpeg2video @ 0xb7321ce8]mb incr damaged
[mpeg2video @ 0xb7321ce8]invalid cbp at 1 32
[mpeg2video @ 0xb7321ce8]mb incr damaged
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 24 34
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 11 35
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 7 36
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 2 37
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 16 38
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 2 39
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 1 40
[mpeg2video @ 0xb7321ce8]invalid cbp at 12 41
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 20 42
[mpeg2video @ 0xb7321ce8]mb incr damaged
[mpeg2video @ 0xb7321ce8]invalid mb type in P Frame at 4 44
[mpeg2video @ 0xb7321ce8]mb incr damaged
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 18 40
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 41 41
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 6 42
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 15 43
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 10 44
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 15
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 16
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 17
[mpeg2video @ 0xb7321ce8]skipped MB in I frame at 1 18
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 19
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 20
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 21
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 22
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 23
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 24
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 25
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 26
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 27
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 28
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 29
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 30
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 31
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 32
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 33
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 34
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 35
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 36
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 37
[mpeg2video @ 0xb7321ce8]invalid mb type in I Frame at 0 38
[mpeg2video @ 0xb7321ce8]invalid mb type in I Frame at 0 39
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 40
[mpeg2video @ 0xb7321ce8]invalid mb type in I Frame at 0 41
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 42
[mpeg2video @ 0xb7321ce8]invalid mb type in I Frame at 0 43
[mpeg2video @ 0xb7321ce8]ac-tex damaged at 0 44
2007-11-28 22:14:59.875 TV: Attempting to change from WatchingPreRecorded to None
2007-11-28 22:14:59.958 TV: Changing from WatchingPreRecorded to None
0: start_time: 4821.642 duration: 323.692
1: start_time: 4821.603 duration: 323.696
stream: start_time: 53573.363 duration: 3597.016 bitrate=11830 kb/s
2007-11-28 22:15:00.026 AFD: Opened codec 0x83aac80, id(MPEG2VIDEO) type(Video)
2007-11-28 22:15:00.027 AFD: Opened codec 0x93faaa0, id(AC3) type(Audio)
0: start_time: 4821.642 duration: 323.692
1: start_time: 4821.603 duration: 323.696
stream: start_time: 53573.363 duration: 3597.016 bitrate=11830 kb/s
2007-11-28 22:15:00.557 AFD: Opened codec 0x93890a0, id(MPEG2VIDEO) type(Video)
2007-11-28 22:15:00.558 AFD: Opened codec 0x83aac80, id(AC3) type(Audio)
0: start_time: 4821.642 duration: 323.692
1: start_time: 4821.603 duration: 323.696
stream: start_time: 53573.363 duration: 3597.016 bitrate=11830 kb/s
2007-11-28 22:15:01.566 AFD: Opened codec 0x93890a0, id(MPEG2VIDEO) type(Video)
2007-11-28 22:15:01.567 AFD: Opened codec 0x83aac80, id(AC3) type(Audio)
0: start_time: 2072.416 duration: 161.692
1: start_time: 2072.407 duration: 161.672
stream: start_time: 23026.750 duration: 1796.668 bitrate=6493 kb/s
2007-11-28 22:15:06.811 AFD: Opened codec 0x83a8930, id(MPEG2VIDEO) type(Video)
2007-11-28 22:15:06.812 AFD: Opened codec 0x93890a0, id(AC3) type(Audio)
0: start_time: 3039.644 duration: 161.697
1: start_time: 3039.606 duration: 161.700
stream: start_time: 33773.395 duration: 1797.056 bitrate=15855 kb/s
2007-11-28 22:15:12.616 AFD: Opened codec 0x8211ab0, id(MPEG2VIDEO) type(Video)
2007-11-28 22:15:12.617 AFD: Opened codec 0x8211df0, id(AC3) type(Audio)
0: start_time: 7417.599 duration: 161.742
1: start_time: 7417.561 duration: 161.744
stream: start_time: 82417.342 duration: 1797.549 bitrate=15859 kb/s
2007-11-28 22:15:15.869 AFD: Opened codec 0x93dc330, id(MPEG2VIDEO) type(Video)
2007-11-28 22:15:15.870 AFD: Opened codec 0x93dcf00, id(AC3) type(Audio)
CC length(21) seq_num(3) 0xcb 0x33 0x8c 0x7 0x9a 0x3b 0xcf 0x0 0x62 0x1f 0x2c 0x92 0x2 0x0 0x91 0x2a 0x0 0x0
Segmentation fault (core dumped)
```

---

### Post by aspenelm on 2007-11-30
I believe I have narrowed the problem to using teletext.  Without the teletext, I haven't had a crash so far watching some prerecorded video.  Since I am hearing impaired I need this feature.  Any ideas on why the teletext is causing it?

With the teletext enabled, only a few videos displayed the captioning correctly. Most of the time the teletext was late, missing words, or new words shown over top of the old ones.

---

### Post by superm1 on 2007-12-01
> **aspenelm said:**
> I believe I have narrowed the problem to using teletext.  Without the teletext, I haven't had a crash so far watching some prerecorded video.  Since I am hearing impaired I need this feature.  Any ideas on why the teletext is causing it?

With the teletext enabled, only a few videos displayed the captioning correctly. Most of the time the teletext was late, missing words, or new words shown over top of the old ones.
Yes.  Set your capture resolution to 720x480.  There is a known issue with it.

---

### Post by aspenelm on 2007-12-03
> **superm1 said:**
> Yes.  Set your capture resolution to 720x480.  There is a known issue with it.

Does that apply for digital recordings? If so where would I find this setting?  I am using the pchdtv 5500 only for digital atsc OTA broadcasts.  It was configured as a dvb card in mythtv-setup.  thanks.

---

### Post by superm1 on 2007-12-03
> **aspenelm said:**
> Does that apply for digital recordings? If so where would I find this setting?  I am using the pchdtv 5500 only for digital atsc OTA broadcasts.  It was configured as a dvb card in mythtv-setup.  thanks.
No, it shouldn't be applicable.

---

### Post by superm1 on 2007-12-03
> **superm1 said:**
> No, it shouldn't be applicable.
If you can, try to play the recordings with a different player and see if the teletext in the stream works correctly.

---

### Post by newlinux on 2007-12-03
I had a problem with the ATSC teletext similar to what you are experiencing. I tried using VBI  CC (sorry I don't really know what the difference is supposed to be) and that worked much better for me on digital recordings.

---

### Post by aspenelm on 2007-12-03
> **superm1 said:**
> If you can, try to play the recordings with a different player and see if the teletext in the stream works correctly.

can you give me an example of a different player?  I've tried mplayer after mounting the recordings directory as a nfs share to the frontend machine. Mplayer plays the audio but the video is scrambled.  Too tired at this point, but will look into mplayer some more tomorrow.

---

### Post by aspenelm on 2007-12-09
Had some time to look at it this weekend.

I have tried Mplayer and Kaffiene/Xine both are now able to playback the recorded streams.  But from what I can tell neither can play or see the teletext (or is it subtitles?).  I have tried all of the video options in each player, xvmc,xv,gl,gl2 etc...with no difference.  

I noticed that the players can use a subtitle file, is this something I can extract from the original recording?  I don't know enough about what software components are involved in getting the teletext to the screen, obviously it exists in the original recorded content.

In mythtv frontend,it is still randomly seg faulting with the teletext enabled, some recordings seem okay others will crash quickly.

Starting to feel out of luck here.

---

### Post by aspenelm on 2008-01-03
Well, I have made some progress unfortuneatly I do not know exactly what fixed it. Captioning is working and stability has greatly improved.

There are just too many factors but I have done the following:
Tried several settings in mythtv for video playback, currently standard and bob2
Tried several video playback programs (mplayer,xine, kaffiene-xine) and adjusting various settings
Tried extracting subtitles with ccextract, which could extract the text but timing was not synced with video
Added weekly mythtv repository for latest updates

I was unaware of differences in captioning, there is ATSC and the regular analog captioning.  For some reason myth frontend now plays the analog captioning and it displays perfectly.  Don't know if the stability is related to the captioning or latest updates in mythtv. Still crashes occassionally.

---

