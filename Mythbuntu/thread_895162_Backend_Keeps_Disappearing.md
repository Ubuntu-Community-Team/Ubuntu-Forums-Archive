---
title: "Backend Keeps Disappearing"
date: 2008-08-19
forum: Mythbuntu
---

### Post by yonkiman on 2008-08-19
I've had my latest Mythbuntu build/box (8.04.1) running for a week or so.  I thought it was stable, but I've been experimenting with different settings, tweaks, etc., a lot, so I might not have noticed the problem I'm about to describe which is:

I went on a week's vacation, set it to record the olympics, and it looks like the backend stopped a day or so after I left.  When I got home, the front end (same box as back end) is complaining it can't connect.  When I do a "mythtv-status", I get 

$ mythtv-status 
Sorry, failed to fetch [http://localhost:6544/xml](http://localhost:6544/xml).

If I run mythtv backend setup (i.e. stop and restart the backend), everything seems to work ok for a while.  Last night it recorded OK but this morning it was in the same state.

Any ideas?  Can anyone tell me what particular logfile might give me a clue as to what is happening?

Thanks...

---

### Post by Loaded.len on 2008-08-20
Can't help you with ***why*** it's crashing, but I can point you to a script that others find useful.  In my previous install of MythDora I had similar problems... Mythbuntu hasn't crashed on me yet in several months.

[http://davemorris.wordpress.com/2008/06/23/keeping-mythtv-backend-alive/](http://davemorris.wordpress.com/2008/06/23/keeping-mythtv-backend-alive/)

NOTE: read the comments for other ways to monitor the backend besides watch

---

### Post by JugeHuge on 2008-08-20
Hello..

Have you checked that you haven't run out of disk space on root mount ??

My Mythtv setup got hosed up because mythtv log files filled root mount. Mount size was 9gig and mythtv logs use 4.5gig of it..

---

### Post by yonkiman on 2008-08-20
> **Loaded.len said:**
> Can't help you with ***why*** it's crashing, but I can point you to a script that others find useful.

Thanks!  That link eventually let me to this wiki entry:
[http://www.mythtv.org/wiki/index.php/StatusMonitoringHowTo]("http://www.mythtv.org/wiki/index.php/StatusMonitoringHowTo")

...apparently I'm not the only person who's run into this.

---

### Post by yonkiman on 2008-08-20
> **JugeHuge said:**
> Have you checked that you haven't run out of disk space on root mount ??

Nope - had 45GB free on root, 800GB free on my new RAID volume.

I'll start poking around the logfiles and see what I can see...

---

### Post by newlinux on 2008-08-20
My backends barely ever fail, but I also use monit for all of them (and other services). Just remember to stop monit when you need to run something that requires mythbackend to not be running (like somethings in mythtv-setup). otherwise, it will restart it :)

---

### Post by yonkiman on 2008-08-22
Here's a logfile from launch until crash (crash was a segmentation fault following this action):
2008-08-22 00:01:42.026 Preview: Grabbed preview '/var/lib/mythtv/recordings/1063_20080821233000.mpg' 720x480@210s

Is this a known problem?

```

<username>@MainMyth:~$ mythbackend
2008-08-21 20:21:02.316 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-21 20:21:02.339 DBHostName is not set in mysql.txt
2008-08-21 20:21:02.339 Assuming localhost
2008-08-21 20:21:02.339 Empty LocalHostName.
2008-08-21 20:21:02.339 Using localhost value of MainMyth
2008-08-21 20:21:02.414 New DB connection, total: 1
2008-08-21 20:21:02.445 Connected to database 'mythconverg' at host: localhost
2008-08-21 20:21:02.446 Closing DB connection named 'DBManager0'
2008-08-21 20:21:02.446 Connected to database 'mythconverg' at host: localhost
2008-08-21 20:21:02.472 New DB connection, total: 2
2008-08-21 20:21:02.472 Connected to database 'mythconverg' at host: localhost
2008-08-21 20:21:02.484 Current Schema Version: 1214
Starting up as the master server.
2008-08-21 20:21:02.681 New DB connection, total: 3
2008-08-21 20:21:02.681 Connected to database 'mythconverg' at host: localhost
2008-08-21 20:21:02.947 New DB scheduler connection
2008-08-21 20:21:02.947 Connected to database 'mythconverg' at host: localhost
2008-08-21 20:21:04.347 Main::Registering HttpStatus Extension
2008-08-21 20:21:04.347 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-08-21 20:21:04.347 Enabled verbose msgs:  important general
2008-08-21 20:21:04.379 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-21 20:21:06.112 Reschedule requested for id -1.
2008-08-21 20:21:12.637 Scheduled 117 items in 6.5 = 5.82 match + 0.70 place
2008-08-21 20:21:12.639 AUTO-Startup assumed
2008-08-21 20:21:12.726 TVRec(2): ASK_RECORDING 2 0 0 0
2008-08-21 20:21:13.144 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-21 20:21:13.166 UPnpMedia: BuildMediaMap Done. Found 0 objects
2008-08-21 20:21:13.471 TVRec(2): Changing from None to RecordingOnly
2008-08-21 20:21:13.611 TVRec(2): HW Tuner: 2->2
2008-08-21 20:21:14.620 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-21 20:21:14.622 Started recording: XXIX Summer Olympics "Track & Field, Diving, Beach Volleyball": channel 2111 on cardid 2, sourceid 2
2008-08-21 20:22:13.012 JobQueue: Commercial Flagging Starting for XXIX Summer Olympics "Track & Field, Diving, Beach Volleyball" recorded from channel 2111 at Thu Aug 21 20:21:00 2008
2008-08-21 20:22:13.143 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-21 20:22:13.143 DBHostName is not set in mysql.txt
2008-08-21 20:22:13.143 Assuming localhost
2008-08-21 20:22:13.144 Empty LocalHostName.
2008-08-21 20:22:13.144 Using localhost value of MainMyth
2008-08-21 20:22:13.149 New DB connection, total: 1
2008-08-21 20:22:13.152 Connected to database 'mythconverg' at host: localhost
2008-08-21 20:22:13.153 Closing DB connection named 'DBManager0'
2008-08-21 20:22:13.155 Connected to database 'mythconverg' at host: localhost
2008-08-21 20:22:13.158 New DB connection, total: 2
2008-08-21 20:22:13.161 Connected to database 'mythconverg' at host: localhost
2008-08-21 20:22:13.225 Connecting to backend server: 192.168.1.100:6543 (try 1 of 5)
2008-08-21 20:22:13.234 Using protocol version 40
2008-08-21 20:22:13.234 MainServer::HandleAnnounce Monitor
2008-08-21 20:22:13.234 adding: MainMyth as a client (events: 0)
2008-08-21 20:22:13.235 MainServer::HandleAnnounce Monitor
2008-08-21 20:22:13.235 adding: MainMyth as a client (events: 1)
2008-08-21 20:22:13.378 AFD: Opened codec 0x849fd0, id(MPEG2VIDEO) type(Video)
2008-08-21 20:22:13.378 AFD: codec AC3 has 6 channels
2008-08-21 20:22:13.378 AFD: Opened codec 0x84a510, id(AC3) type(Audio)
2008-08-21 20:22:22.958 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-21 20:22:31.959 TFW, Error: Write() -- IOBOUND begin cnt(9400) free(963)
2008-08-21 20:22:31.970 TFW, Error: Write() -- IOBOUND end
2008-08-21 20:22:38.053 TFW, Error: Write() -- IOBOUND begin cnt(9400) free(8859)
2008-08-21 20:22:38.982 TFW, Error: Write() -- IOBOUND end
2008-08-21 20:30:04.862 MainServer::HandleAnnounce Monitor
2008-08-21 20:30:04.862 adding: MainMyth as a client (events: 0)
2008-08-21 20:37:23.031 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-21 20:40:02.831 MainServer::HandleAnnounce Monitor
2008-08-21 20:40:02.831 adding: MainMyth as a client (events: 0)
2008-08-21 20:50:03.226 MainServer::HandleAnnounce Monitor
2008-08-21 20:50:03.226 adding: MainMyth as a client (events: 0)
2008-08-21 20:51:18.169 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-21 20:51:18.199 UPnpMedia: BuildMediaMap Done. Found 0 objects
2008-08-21 20:52:23.100 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-21 21:00:02.054 MainServer::HandleAnnounce Monitor
2008-08-21 21:00:02.054 adding: MainMyth as a client (events: 0)
2008-08-21 21:02:46.304 [mpeg2video @ 0x7faeba6645b0]00 motion_type at 49 63
2008-08-21 21:02:46.305 [mpeg2video @ 0x7faeba6645b0]Warning MVs not available
2008-08-21 21:02:46.318 [mpeg2video @ 0x7faeba6645b0]ac-tex damaged at 85 7
2008-08-21 21:02:46.319 [mpeg2video @ 0x7faeba6645b0]00 motion_type at 70 37
2008-08-21 21:02:46.319 [mpeg2video @ 0x7faeba6645b0]00 motion_type at 24 9
2008-08-21 21:02:46.319 [mpeg2video @ 0x7faeba6645b0]00 motion_type at 77 12
2008-08-21 21:02:46.320 [mpeg2video @ 0x7faeba6645b0]00 motion_type at 69 40
2008-08-21 21:02:46.321 [mpeg2video @ 0x7faeba6645b0]00 motion_type at 69 20
2008-08-21 21:02:46.322 [mpeg2video @ 0x7faeba6645b0]ac-tex damaged at 27 24
2008-08-21 21:02:46.322 [mpeg2video @ 0x7faeba6645b0]00 motion_type at 32 25
2008-08-21 21:06:34.250 MainServer::HandleAnnounce Monitor
2008-08-21 21:06:34.250 adding: MainMyth as a client (events: 0)
2008-08-21 21:06:34.250 MainServer::HandleAnnounce Monitor
2008-08-21 21:06:34.250 adding: MainMyth as a client (events: 1)
2008-08-21 21:06:40.101 MainServer::HandleAnnounce Playback
2008-08-21 21:06:40.101 adding: MainMyth as a client (events: 0)
2008-08-21 21:06:40.101 MainServer::HandleAnnounce FileTransfer
2008-08-21 21:06:40.101 adding: MainMyth as a remote file transfer
2008-08-21 21:06:52.166 MainServer::HandleAnnounce Playback
2008-08-21 21:06:52.167 adding: MainMyth as a client (events: 0)
2008-08-21 21:06:52.167 MainServer::HandleAnnounce FileTransfer
2008-08-21 21:06:52.167 adding: MainMyth as a remote file transfer
2008-08-21 21:07:19.451 MainServer::HandleAnnounce Playback
2008-08-21 21:07:19.451 adding: MainMyth as a client (events: 0)
2008-08-21 21:07:19.452 MainServer::HandleAnnounce FileTransfer
2008-08-21 21:07:19.452 adding: MainMyth as a remote file transfer
2008-08-21 21:07:23.200 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-21 21:07:25.467 MainServer::HandleAnnounce Playback
2008-08-21 21:07:25.467 adding: MainMyth as a client (events: 0)
2008-08-21 21:07:25.468 MainServer::HandleAnnounce FileTransfer
2008-08-21 21:07:25.468 adding: MainMyth as a remote file transfer
2008-08-21 21:10:02.590 MainServer::HandleAnnounce Monitor
2008-08-21 21:10:02.590 adding: MainMyth as a client (events: 0)
2008-08-21 21:20:03.127 MainServer::HandleAnnounce Monitor
2008-08-21 21:20:03.127 adding: MainMyth as a client (events: 0)
2008-08-21 21:21:20.201 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-21 21:21:20.241 UPnpMedia: BuildMediaMap Done. Found 0 objects
2008-08-21 21:22:23.290 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-21 21:28:30.045 Reschedule requested for id 0.
2008-08-21 21:28:32.965 Scheduled 117 items in 2.9 = 0.00 match + 2.92 place
2008-08-21 21:29:00.013 TVRec(1): ASK_RECORDING 1 29 0 0
2008-08-21 21:29:31.326 TVRec(1): Changing from None to RecordingOnly
2008-08-21 21:29:31.328 TVRec(1): HW Tuner: 1->1
2008-08-21 21:29:31.499 MPEGRec(/dev/video0) Warning: Audio sample rate 32000 Hz
			is not supported by ivtv driver, using 48000 Hz instead.
2008-08-21 21:29:31.575 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 10 min
2008-08-21 21:29:31.576 Started recording: South Park "Follow That Egg!": channel 1063 on cardid 1, sourceid 1
 *********************** WARNING ***********************
 ivtv drivers prior to 0.10.0 can cause lockups when    
 reading VBI. Drivers between 0.10.5 and 1.0.3+ do not  
 properly capture VBI data on PVR-250 and PVR-350 cards.

2008-08-21 21:30:03.673 MainServer::HandleAnnounce Monitor
2008-08-21 21:30:03.673 adding: MainMyth as a client (events: 0)
2008-08-21 21:37:23.415 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 10 min
2008-08-21 21:40:02.677 MainServer::HandleAnnounce Monitor
2008-08-21 21:40:02.677 adding: MainMyth as a client (events: 0)
2008-08-21 21:47:23.542 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 10 min
2008-08-21 21:50:03.722 MainServer::HandleAnnounce Monitor
2008-08-21 21:50:03.722 adding: MainMyth as a client (events: 0)
2008-08-21 21:51:22.254 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-21 21:51:22.276 UPnpMedia: BuildMediaMap Done. Found 0 objects
2008-08-21 21:52:11.625 [mpeg2video @ 0x7faeba6645b0]ac-tex damaged at 44 49
2008-08-21 21:52:11.628 [mpeg2video @ 0x7faeba6645b0]ac-tex damaged at 78 67
2008-08-21 21:52:11.651 [mpeg2video @ 0x7faeba6645b0]mb incr damaged
2008-08-21 21:52:11.651 [mpeg2video @ 0x7faeba6645b0]00 motion_type at 110 42
2008-08-21 21:52:11.657 [mpeg2video @ 0x7faeba6645b0]00 motion_type at 36 3
2008-08-21 21:52:11.658 [mpeg2video @ 0x7faeba6645b0]mb incr damaged
2008-08-21 21:52:11.660 [mpeg2video @ 0x7faeba6645b0]00 motion_type at 40 22
2008-08-21 21:52:11.661 [mpeg2video @ 0x7faeba6645b0]mb incr damaged
2008-08-21 21:52:11.663 [mpeg2video @ 0x7faeba6645b0]Warning MVs not available
2008-08-21 21:55:34.542 [mpeg2video @ 0x7faeba6645b0]ac-tex damaged at 114 36
2008-08-21 21:57:23.608 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 10 min
2008-08-21 22:00:03.442 MainServer::HandleAnnounce Monitor
2008-08-21 22:00:03.442 adding: MainMyth as a client (events: 0)
2008-08-21 22:00:30.187 TVRec(1): Changing from RecordingOnly to None
2008-08-21 22:00:30.227 Finished recording South Park "Follow That Egg!": channel 1063
2008-08-21 22:00:30.335 Reschedule requested for id 0.
2008-08-21 22:00:31.029 Finished recording South Park "Follow That Egg!": channel 1063
2008-08-21 22:00:32.071 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-21 22:00:32.091 RingBuf(/var/lib/mythtv/recordings/2111_20080821202100.mpg): Waited 1.0 seconds for data to become available...
2008-08-21 22:00:32.195 DBHostName is not set in mysql.txt
2008-08-21 22:00:32.195 Assuming localhost
2008-08-21 22:00:32.195 Empty LocalHostName.
2008-08-21 22:00:32.195 Using localhost value of MainMyth
2008-08-21 22:00:32.498 New DB connection, total: 1
2008-08-21 22:00:32.501 Connected to database 'mythconverg' at host: localhost
2008-08-21 22:00:32.501 Closing DB connection named 'DBManager0'
2008-08-21 22:00:32.501 Connected to database 'mythconverg' at host: localhost
2008-08-21 22:00:32.502 New DB connection, total: 2
2008-08-21 22:00:32.502 Connected to database 'mythconverg' at host: localhost
2008-08-21 22:00:32.606 Current Schema Version: 1214
2008-08-21 22:00:32.867 Scheduled 116 items in 2.5 = 0.00 match + 2.52 place
2008-08-21 22:00:35.366 AFD: Opened codec 0x8d63c0, id(MPEG2VIDEO) type(Video)
2008-08-21 22:00:35.366 AFD: codec MP2 has 2 channels
2008-08-21 22:00:35.367 AFD: Opened codec 0x8d77f0, id(MP2) type(Audio)
2008-08-21 22:00:35.583 Preview: Grabbed preview '/var/lib/mythtv/recordings/1063_20080821213000.mpg' 720x480@210s
2008-08-21 22:07:23.724 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-21 22:07:23.735 Expiring 1155 MBytes for 1063 @ Thu Aug 7 21:30:00 2008 => South Park.  Too many episodes, we only want to keep 8.
2008-08-21 22:07:23.767 Reschedule requested for id 0.
2008-08-21 22:07:23.947 Scheduled 116 items in 0.2 = 0.00 match + 0.18 place
2008-08-21 22:07:31.055 Reschedule requested for id 0.
2008-08-21 22:07:31.209 Scheduled 116 items in 0.2 = 0.00 match + 0.15 place
2008-08-21 22:10:03.970 MainServer::HandleAnnounce Monitor
2008-08-21 22:10:03.970 adding: MainMyth as a client (events: 0)
2008-08-21 22:20:02.906 MainServer::HandleAnnounce Monitor
2008-08-21 22:20:02.906 adding: MainMyth as a client (events: 0)
2008-08-21 22:21:27.278 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-21 22:21:27.293 UPnpMedia: BuildMediaMap Done. Found 0 objects
2008-08-21 22:22:23.876 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-21 22:28:42.473 [mpeg2video @ 0x7faeba6645b0]slice mismatch
2008-08-21 22:30:03.261 MainServer::HandleAnnounce Monitor
2008-08-21 22:30:03.261 adding: MainMyth as a client (events: 0)
2008-08-21 22:37:23.960 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-21 22:40:03.190 MainServer::HandleAnnounce Monitor
2008-08-21 22:40:03.190 adding: MainMyth as a client (events: 0)
2008-08-21 22:50:03.484 MainServer::HandleAnnounce Monitor
2008-08-21 22:50:03.484 adding: MainMyth as a client (events: 0)
2008-08-21 22:51:31.295 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-21 22:51:31.309 UPnpMedia: BuildMediaMap Done. Found 0 objects
2008-08-21 22:52:24.051 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-21 22:53:20.840 RingBuf(/var/lib/mythtv/recordings/2111_20080821202100.mpg): Waited 1.0 seconds for data to become available...
2008-08-21 22:53:26.629 TFW, Error: Write() -- IOBOUND begin cnt(9400) free(3971)
2008-08-21 22:53:26.923 [mpeg2video @ 0x7faeba6645b0]ac-tex damaged at 19 59
2008-08-21 22:53:28.345 TFW, Error: Write() -- IOBOUND end
2008-08-21 22:53:28.354 TFW, Error: Write() -- IOBOUND begin cnt(9400) free(5299)
2008-08-21 22:53:28.489 TFW, Error: Write() -- IOBOUND end
2008-08-21 22:53:31.446 TFW, Error: Write() -- IOBOUND begin cnt(9400) free(2091)
2008-08-21 22:53:32.140 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-21 22:53:32.183 DBHostName is not set in mysql.txt
2008-08-21 22:53:32.183 Assuming localhost
2008-08-21 22:53:32.183 Empty LocalHostName.
2008-08-21 22:53:32.183 Using localhost value of MainMyth
2008-08-21 22:53:32.491 New DB connection, total: 1
2008-08-21 22:53:32.495 Connected to database 'mythconverg' at host: localhost
2008-08-21 22:53:32.496 Closing DB connection named 'DBManager0'
2008-08-21 22:53:32.496 Connected to database 'mythconverg' at host: localhost
2008-08-21 22:53:32.497 New DB connection, total: 2
2008-08-21 22:53:32.497 Connected to database 'mythconverg' at host: localhost
2008-08-21 22:53:32.625 Current Schema Version: 1214
2008-08-21 22:53:34.849 TFW, Error: Write() -- IOBOUND end
2008-08-21 22:53:35.907 AFD: Opened codec 0x8e9110, id(MPEG2VIDEO) type(Video)
2008-08-21 22:53:35.907 AFD: codec AC3 has 6 channels
2008-08-21 22:53:35.908 AFD: Opened codec 0x8e9650, id(AC3) type(Audio)
2008-08-21 22:53:37.952 Preview: Grabbed preview '/var/lib/mythtv/recordings/2111_20080821202100.mpg' 1920x1088@210s
2008-08-21 22:54:18.626 JobQueue: Commercial Flagging Starting for South Park "Follow That Egg!" recorded from channel 1063 at Thu Aug 21 21:30:00 2008
2008-08-21 22:54:18.744 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-21 22:54:18.744 DBHostName is not set in mysql.txt
2008-08-21 22:54:18.744 Assuming localhost
2008-08-21 22:54:18.744 Empty LocalHostName.
2008-08-21 22:54:18.744 Using localhost value of MainMyth
2008-08-21 22:54:18.750 New DB connection, total: 1
2008-08-21 22:54:18.752 Connected to database 'mythconverg' at host: localhost
2008-08-21 22:54:18.753 Closing DB connection named 'DBManager0'
2008-08-21 22:54:18.753 Connected to database 'mythconverg' at host: localhost
2008-08-21 22:54:18.756 New DB connection, total: 2
2008-08-21 22:54:18.756 Connected to database 'mythconverg' at host: localhost
2008-08-21 22:54:18.769 Connecting to backend server: 192.168.1.100:6543 (try 1 of 5)
2008-08-21 22:54:18.774 Using protocol version 40
2008-08-21 22:54:18.774 MainServer::HandleAnnounce Monitor
2008-08-21 22:54:18.774 adding: MainMyth as a client (events: 0)
2008-08-21 22:54:18.775 MainServer::HandleAnnounce Monitor
2008-08-21 22:54:18.775 adding: MainMyth as a client (events: 1)
2008-08-21 22:54:19.194 AFD: Opened codec 0x837440, id(MPEG2VIDEO) type(Video)
2008-08-21 22:54:19.194 AFD: codec MP2 has 2 channels
2008-08-21 22:54:19.194 AFD: Opened codec 0x838870, id(MP2) type(Audio)
2008-08-21 22:56:41.716 [mpeg2video @ 0x7f1dd6bb95b0]ac-tex damaged at 23 6
2008-08-21 22:56:41.716 [mpeg2video @ 0x7f1dd6bb95b0]Warning MVs not available
2008-08-21 22:56:42.318 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-21 22:56:42.318 DBHostName is not set in mysql.txt
2008-08-21 22:56:42.318 Assuming localhost
2008-08-21 22:56:42.318 Empty LocalHostName.
2008-08-21 22:56:42.318 Using localhost value of MainMyth
2008-08-21 22:56:42.324 New DB connection, total: 1
2008-08-21 22:56:42.326 Connected to database 'mythconverg' at host: localhost
2008-08-21 22:56:42.327 Closing DB connection named 'DBManager0'
2008-08-21 22:56:42.327 Connected to database 'mythconverg' at host: localhost
2008-08-21 22:56:42.328 New DB connection, total: 2
2008-08-21 22:56:42.328 Connected to database 'mythconverg' at host: localhost
2008-08-21 22:56:42.329 Current Schema Version: 1214
2008-08-21 22:56:42.516 AFD: Opened codec 0x8d63c0, id(MPEG2VIDEO) type(Video)
2008-08-21 22:56:42.516 AFD: codec MP2 has 2 channels
2008-08-21 22:56:42.516 AFD: Opened codec 0x8d77f0, id(MP2) type(Audio)
2008-08-21 22:56:42.696 Preview: Grabbed preview '/var/lib/mythtv/recordings/1063_20080821213000.mpg' 720x480@210s
2008-08-21 22:57:30.509 Reschedule requested for id 0.
2008-08-21 22:57:31.724 Scheduled 116 items in 1.2 = 0.00 match + 1.21 place
2008-08-21 22:58:00.344 TVRec(1): ASK_RECORDING 1 29 0 0
2008-08-21 22:58:31.983 TVRec(1): Changing from None to RecordingOnly
2008-08-21 22:58:31.997 TVRec(1): HW Tuner: 1->1
2008-08-21 22:58:32.069 MPEGRec(/dev/video0) Warning: Audio sample rate 32000 Hz
			is not supported by ivtv driver, using 48000 Hz instead.
 *********************** WARNING ***********************
 ivtv drivers prior to 0.10.0 can cause lockups when    
 reading VBI. Drivers between 0.10.5 and 1.0.3+ do not  
 properly capture VBI data on PVR-250 and PVR-350 cards.

2008-08-21 22:58:32.248 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 10 min
2008-08-21 22:58:32.264 Started recording: The Daily Show With Jon Stewart: channel 1063 on cardid 1, sourceid 1
2008-08-21 22:59:23.647 JobQueue: Commercial Flagging Starting for The Daily Show With Jon Stewart recorded from channel 1063 at Thu Aug 21 22:59:00 2008
2008-08-21 22:59:23.786 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-21 22:59:23.787 DBHostName is not set in mysql.txt
2008-08-21 22:59:23.787 Assuming localhost
2008-08-21 22:59:23.787 Empty LocalHostName.
2008-08-21 22:59:23.787 Using localhost value of MainMyth
2008-08-21 22:59:23.843 New DB connection, total: 1
2008-08-21 22:59:23.846 Connected to database 'mythconverg' at host: localhost
2008-08-21 22:59:23.847 Closing DB connection named 'DBManager0'
2008-08-21 22:59:23.847 Connected to database 'mythconverg' at host: localhost
2008-08-21 22:59:23.851 New DB connection, total: 2
2008-08-21 22:59:23.852 Connected to database 'mythconverg' at host: localhost
2008-08-21 22:59:23.880 Connecting to backend server: 192.168.1.100:6543 (try 1 of 5)
2008-08-21 22:59:23.881 Using protocol version 40
2008-08-21 22:59:23.881 MainServer::HandleAnnounce Monitor
2008-08-21 22:59:23.881 adding: MainMyth as a client (events: 0)
2008-08-21 22:59:23.881 MainServer::HandleAnnounce Monitor
2008-08-21 22:59:23.881 adding: MainMyth as a client (events: 1)
2008-08-21 22:59:32.017 AFD: Opened codec 0x8388d0, id(MPEG2VIDEO) type(Video)
2008-08-21 22:59:32.017 AFD: codec MP2 has 2 channels
2008-08-21 22:59:32.017 AFD: Opened codec 0x839d00, id(MP2) type(Audio)
2008-08-21 23:00:04.670 MainServer::HandleAnnounce Monitor
2008-08-21 23:00:04.670 adding: MainMyth as a client (events: 0)
2008-08-21 23:07:24.168 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 10 min
2008-08-21 23:10:03.939 MainServer::HandleAnnounce Monitor
2008-08-21 23:10:03.939 adding: MainMyth as a client (events: 0)
2008-08-21 23:17:24.234 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 10 min
2008-08-21 23:20:02.721 MainServer::HandleAnnounce Monitor
2008-08-21 23:20:02.721 adding: MainMyth as a client (events: 0)
2008-08-21 23:21:34.310 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-21 23:21:34.326 UPnpMedia: BuildMediaMap Done. Found 0 objects
2008-08-21 23:27:24.332 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 10 min
2008-08-21 23:28:30.360 Reschedule requested for id 0.
2008-08-21 23:28:31.947 Scheduled 116 items in 1.6 = 0.00 match + 1.59 place
2008-08-21 23:29:30.756 TVRec(1): ASK_RECORDING 1 29 0 0
2008-08-21 23:30:03.071 TVRec(1): Changing from RecordingOnly to None
2008-08-21 23:30:03.111 Finished recording The Daily Show With Jon Stewart: channel 1063
2008-08-21 23:30:03.381 Finished recording The Daily Show With Jon Stewart: channel 1063
2008-08-21 23:30:04.073 TVRec(1): Changing from None to RecordingOnly
2008-08-21 23:30:04.098 TVRec(1): HW Tuner: 1->1
2008-08-21 23:30:04.452 MPEGRec(/dev/video0) Warning: Audio sample rate 32000 Hz
			is not supported by ivtv driver, using 48000 Hz instead.
 *********************** WARNING ***********************
 ivtv drivers prior to 0.10.0 can cause lockups when    
 reading VBI. Drivers between 0.10.5 and 1.0.3+ do not  
 properly capture VBI data on PVR-250 and PVR-350 cards.

2008-08-21 23:30:04.833 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 10 min
2008-08-21 23:30:04.834 Started recording: The Colbert Report: channel 1063 on cardid 1, sourceid 1
2008-08-21 23:30:05.373 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-21 23:30:05.496 DBHostName is not set in mysql.txt
2008-08-21 23:30:05.496 Assuming localhost
2008-08-21 23:30:05.496 Empty LocalHostName.
2008-08-21 23:30:05.496 Using localhost value of MainMyth
2008-08-21 23:30:05.602 New DB connection, total: 1
2008-08-21 23:30:05.644 Connected to database 'mythconverg' at host: localhost
2008-08-21 23:30:05.644 Closing DB connection named 'DBManager0'
2008-08-21 23:30:05.644 Connected to database 'mythconverg' at host: localhost
2008-08-21 23:30:05.645 New DB connection, total: 2
2008-08-21 23:30:05.652 Connected to database 'mythconverg' at host: localhost
2008-08-21 23:30:05.653 Current Schema Version: 1214
2008-08-21 23:30:05.837 Reschedule requested for id 0.
2008-08-21 23:30:06.269 Scheduled 115 items in 0.4 = 0.00 match + 0.43 place
2008-08-21 23:30:06.607 MainServer::HandleAnnounce Monitor
2008-08-21 23:30:06.607 adding: MainMyth as a client (events: 0)
2008-08-21 23:30:08.723 AFD: Opened codec 0x8d6200, id(MPEG2VIDEO) type(Video)
2008-08-21 23:30:08.723 AFD: codec MP2 has 2 channels
2008-08-21 23:30:08.723 AFD: Opened codec 0x8d7630, id(MP2) type(Audio)
2008-08-21 23:30:08.955 Preview: Grabbed preview '/var/lib/mythtv/recordings/1063_20080821225900.mpg' 720x480@210s
2008-08-21 23:30:11.820 [mpeg2video @ 0x7f0c3181a5b0]ac-tex damaged at 19 22
2008-08-21 23:30:11.820 [mpeg2video @ 0x7f0c3181a5b0]Warning MVs not available
2008-08-21 23:30:12.251 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-21 23:30:12.252 DBHostName is not set in mysql.txt
2008-08-21 23:30:12.252 Assuming localhost
2008-08-21 23:30:12.252 Empty LocalHostName.
2008-08-21 23:30:12.252 Using localhost value of MainMyth
2008-08-21 23:30:12.258 New DB connection, total: 1
2008-08-21 23:30:12.260 Connected to database 'mythconverg' at host: localhost
2008-08-21 23:30:12.261 Closing DB connection named 'DBManager0'
2008-08-21 23:30:12.262 Connected to database 'mythconverg' at host: localhost
2008-08-21 23:30:12.263 New DB connection, total: 2
2008-08-21 23:30:12.263 Connected to database 'mythconverg' at host: localhost
2008-08-21 23:30:12.264 Current Schema Version: 1214
2008-08-21 23:30:14.695 AFD: Opened codec 0x8d61c0, id(MPEG2VIDEO) type(Video)
2008-08-21 23:30:14.695 AFD: codec MP2 has 2 channels
2008-08-21 23:30:14.695 AFD: Opened codec 0x8d75f0, id(MP2) type(Audio)
2008-08-21 23:30:14.755 Preview: Grabbed preview '/var/lib/mythtv/recordings/1063_20080821225900.mpg' 720x480@210s
2008-08-21 23:30:28.747 JobQueue: Commercial Flagging Starting for The Colbert Report recorded from channel 1063 at Thu Aug 21 23:30:00 2008
2008-08-21 23:30:28.876 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-21 23:30:28.876 DBHostName is not set in mysql.txt
2008-08-21 23:30:28.876 Assuming localhost
2008-08-21 23:30:28.877 Empty LocalHostName.
2008-08-21 23:30:28.877 Using localhost value of MainMyth
2008-08-21 23:30:28.882 New DB connection, total: 1
2008-08-21 23:30:28.885 Connected to database 'mythconverg' at host: localhost
2008-08-21 23:30:28.885 Closing DB connection named 'DBManager0'
2008-08-21 23:30:28.885 Connected to database 'mythconverg' at host: localhost
2008-08-21 23:30:28.888 New DB connection, total: 2
2008-08-21 23:30:28.889 Connected to database 'mythconverg' at host: localhost
2008-08-21 23:30:28.898 Connecting to backend server: 192.168.1.100:6543 (try 1 of 5)
2008-08-21 23:30:28.898 Using protocol version 40
2008-08-21 23:30:28.898 MainServer::HandleAnnounce Monitor
2008-08-21 23:30:28.898 adding: MainMyth as a client (events: 0)
2008-08-21 23:30:28.899 MainServer::HandleAnnounce Monitor
2008-08-21 23:30:28.899 adding: MainMyth as a client (events: 1)
2008-08-21 23:30:31.215 AFD: Opened codec 0x8388c0, id(MPEG2VIDEO) type(Video)
2008-08-21 23:30:31.215 AFD: codec MP2 has 2 channels
2008-08-21 23:30:31.216 AFD: Opened codec 0x839cf0, id(MP2) type(Audio)
2008-08-21 23:37:24.399 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 10 min
2008-08-21 23:37:24.418 Expiring 1175 MBytes for 1063 @ Thu Jul 17 22:59:00 2008 => The Daily Show With Jon Stewart.  Too many episodes, we only want to keep 10.
2008-08-21 23:37:24.440 Reschedule requested for id 0.
2008-08-21 23:37:24.589 Scheduled 115 items in 0.1 = 0.00 match + 0.15 place
2008-08-21 23:37:31.992 Reschedule requested for id 0.
2008-08-21 23:37:31.996 Connecting to backend server: 192.168.1.100:6543 (try 1 of 5)
2008-08-21 23:37:31.997 Using protocol version 40
2008-08-21 23:37:31.997 MainServer::HandleAnnounce Monitor
2008-08-21 23:37:31.997 adding: MainMyth as a client (events: 0)
2008-08-21 23:37:31.998 MainServer::HandleAnnounce Monitor
2008-08-21 23:37:31.998 adding: MainMyth as a client (events: 1)
2008-08-21 23:37:32.000 GetRecordBasename found no entry
2008-08-21 23:37:32.131 Scheduled 115 items in 0.1 = 0.00 match + 0.14 place
2008-08-21 23:40:03.104 MainServer::HandleAnnounce Monitor
2008-08-21 23:40:03.104 adding: MainMyth as a client (events: 0)
2008-08-21 23:47:24.532 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 10 min
2008-08-21 23:50:03.607 MainServer::HandleAnnounce Monitor
2008-08-21 23:50:03.607 adding: MainMyth as a client (events: 0)
2008-08-21 23:51:35.330 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-21 23:51:35.355 UPnpMedia: BuildMediaMap Done. Found 0 objects
2008-08-21 23:57:24.678 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 10 min
2008-08-22 00:00:03.335 MainServer::HandleAnnounce Monitor
2008-08-22 00:00:03.335 adding: MainMyth as a client (events: 0)
2008-08-22 00:00:30.500 TVRec(2): Changing from RecordingOnly to None
2008-08-22 00:00:30.531 Finished recording XXIX Summer Olympics "Track & Field, Diving, Beach Volleyball": channel 2111
2008-08-22 00:00:30.562 Reschedule requested for id 0.
2008-08-22 00:00:31.656 Finished recording XXIX Summer Olympics "Track & Field, Diving, Beach Volleyball": channel 2111
2008-08-22 00:00:33.710 Scheduled 113 items in 3.1 = 0.00 match + 3.15 place
2008-08-22 00:00:34.031 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-22 00:00:34.106 DBHostName is not set in mysql.txt
2008-08-22 00:00:34.106 Assuming localhost
2008-08-22 00:00:34.106 Empty LocalHostName.
2008-08-22 00:00:34.106 Using localhost value of MainMyth
2008-08-22 00:00:34.218 New DB connection, total: 1
2008-08-22 00:00:34.222 Connected to database 'mythconverg' at host: localhost
2008-08-22 00:00:34.222 Closing DB connection named 'DBManager0'
2008-08-22 00:00:34.223 Connected to database 'mythconverg' at host: localhost
2008-08-22 00:00:34.225 New DB connection, total: 2
2008-08-22 00:00:34.225 Connected to database 'mythconverg' at host: localhost
2008-08-22 00:00:34.240 Current Schema Version: 1214
2008-08-22 00:00:36.991 AFD: Opened codec 0x8e9150, id(MPEG2VIDEO) type(Video)
2008-08-22 00:00:36.991 AFD: codec AC3 has 6 channels
2008-08-22 00:00:36.993 AFD: Opened codec 0x8e9690, id(AC3) type(Audio)
2008-08-22 00:00:37.970 Preview: Grabbed preview '/var/lib/mythtv/recordings/2111_20080821202100.mpg' 1920x1088@210s
2008-08-22 00:01:30.294 TVRec(1): Changing from RecordingOnly to None
2008-08-22 00:01:30.297 Finished recording The Colbert Report: channel 1063
2008-08-22 00:01:30.317 Reschedule requested for id 0.
2008-08-22 00:01:30.520 Scheduled 112 items in 0.2 = 0.00 match + 0.20 place
2008-08-22 00:01:30.672 Finished recording The Colbert Report: channel 1063
2008-08-22 00:01:30.939 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-22 00:01:30.941 DBHostName is not set in mysql.txt
2008-08-22 00:01:30.941 Assuming localhost
2008-08-22 00:01:30.941 Empty LocalHostName.
2008-08-22 00:01:30.941 Using localhost value of MainMyth
2008-08-22 00:01:30.965 New DB connection, total: 1
2008-08-22 00:01:31.063 Connected to database 'mythconverg' at host: localhost
2008-08-22 00:01:31.063 Closing DB connection named 'DBManager0'
2008-08-22 00:01:31.066 Connected to database 'mythconverg' at host: localhost
2008-08-22 00:01:31.078 New DB connection, total: 2
2008-08-22 00:01:31.091 Connected to database 'mythconverg' at host: localhost
2008-08-22 00:01:31.114 Current Schema Version: 1214
2008-08-22 00:01:33.801 AFD: Opened codec 0x8d61d0, id(MPEG2VIDEO) type(Video)
2008-08-22 00:01:33.801 AFD: codec MP2 has 2 channels
2008-08-22 00:01:33.801 AFD: Opened codec 0x8d7600, id(MP2) type(Audio)
2008-08-22 00:01:34.016 Preview: Grabbed preview '/var/lib/mythtv/recordings/1063_20080821233000.mpg' 720x480@210s
2008-08-22 00:01:38.194 [mpeg2video @ 0x7fde00bc25b0]ac-tex damaged at 20 10
2008-08-22 00:01:38.194 [mpeg2video @ 0x7fde00bc25b0]Warning MVs not available
2008-08-22 00:01:39.075 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-22 00:01:39.076 DBHostName is not set in mysql.txt
2008-08-22 00:01:39.076 Assuming localhost
2008-08-22 00:01:39.076 Empty LocalHostName.
2008-08-22 00:01:39.076 Using localhost value of MainMyth
2008-08-22 00:01:39.082 New DB connection, total: 1
2008-08-22 00:01:39.086 Connected to database 'mythconverg' at host: localhost
2008-08-22 00:01:39.088 Closing DB connection named 'DBManager0'
2008-08-22 00:01:39.088 Connected to database 'mythconverg' at host: localhost
2008-08-22 00:01:39.089 New DB connection, total: 2
2008-08-22 00:01:39.090 Connected to database 'mythconverg' at host: localhost
2008-08-22 00:01:39.091 Current Schema Version: 1214
2008-08-22 00:01:41.551 AFD: Opened codec 0x8d6180, id(MPEG2VIDEO) type(Video)
2008-08-22 00:01:41.551 AFD: codec MP2 has 2 channels
2008-08-22 00:01:41.551 AFD: Opened codec 0x8d75b0, id(MP2) type(Audio)
2008-08-22 00:01:42.026 Preview: Grabbed preview '/var/lib/mythtv/recordings/1063_20080821233000.mpg' 720x480@210s
Segmentation fault

```

---

