---
title: "Unable to watch recordings on remote Frontend"
date: 2008-10-10
forum: Mythbuntu
---

### Post by dcwdrum on 2008-10-10
Hi Everyone,

I've been running a combined backend/frontend machine for about a year now and it has been running flawlessly...(for the most part).  I recently decided to branch out and put together a frontend only machine for the bedroom.  Right now I'm just testing out the new hardware with a copy of Knoppmyth but am running into some problems.

On the second frontend, it connects to the mysql database just fine and I can watch Live TV with no problem.  What I can't figure out is when I go to watch a recording, all of the recordings show up like they usually do (even the video preview) but when I try to play one, the screen goes black for a second or two and then it returns me back to the Watch Recordings menu.

Does anyone know why this is happening?  Is there a setting that I'm missing?

Stats:
-Backend/Frontend running Mythbuntu 8.04
-Frontend running Knoppmyth R5.5
-Gigabit Ethernet connecting everything

Thanks!

---

### Post by newlinux on 2008-10-10
Seeing the frontend and backend logs when this happens will help us help you.

---

### Post by dcwdrum on 2008-10-10
Hello,

Here is a section of the backend log that includes the time frame that I was using the remote frontend.

The host name of the combo box is mythBox
and the host name of the remote frontend is testMyth.

Since I'm "testing" the remote frontend by running a live CD, I wasn't able to find any frontend logs.  Hopefully the log below will be enough.  During the sesions below I started to watch Live TV and that was successful.  I then quit the live TV and tried to watch a recorded show, of to which that failed.

```
2008-10-10 23:00:12.293 Using localhost value of mythBox
2008-10-10 23:00:12.350 New DB connection, total: 1
2008-10-10 23:00:12.423 Connected to database 'mythconverg' at host: localhost
2008-10-10 23:00:12.486 Closing DB connection named 'DBManager0'
2008-10-10 23:00:12.507 Connected to database 'mythconverg' at host: localhost
2008-10-10 23:00:12.509 New DB connection, total: 2
2008-10-10 23:00:12.511 Connected to database 'mythconverg' at host: localhost
2008-10-10 23:00:12.514 Current Schema Version: 1214
2008-10-10 23:00:14.841 Scheduled 386 items in 3.8 = 0.01 match + 3.81 place
2008-10-10 23:00:15.546 AFD: Opened codec 0x829ef50, id(MPEG2VIDEO) type(Video)
2008-10-10 23:00:15.551 AFD: codec MP2 has 2 channels
2008-10-10 23:00:15.551 AFD: Opened codec 0x829f2c0, id(MP2) type(Audio)
2008-10-10 23:00:15.796 Preview: Grabbed preview '/mythtv/disk2/recordings/1003_20081010220000.mpg' 720x480@74s
2008-10-10 23:01:01.610 JobQueue: Commercial Flagging Starting for NUMB3RS "The Decoy Effect" recorded from channel 1003 at Fri Oct 10 22:00:00 2008
2008-10-10 23:01:01.838 Using runtime prefix = /usr, libdir = /usr/lib
2008-10-10 23:01:01.842 Empty LocalHostName.
2008-10-10 23:01:01.843 Using localhost value of mythBox
2008-10-10 23:01:01.852 New DB connection, total: 1
2008-10-10 23:01:01.859 Connected to database 'mythconverg' at host: localhost
2008-10-10 23:01:01.862 Closing DB connection named 'DBManager0'
2008-10-10 23:01:01.863 Connected to database 'mythconverg' at host: localhost
2008-10-10 23:01:01.868 New DB connection, total: 2
2008-10-10 23:01:01.870 Connected to database 'mythconverg' at host: localhost
2008-10-10 23:01:01.891 Connecting to backend server: 192.168.2.2:6543 (try 1 of 5)
2008-10-10 23:01:01.894 Using protocol version 40
2008-10-10 23:01:01.895 MainServer::HandleAnnounce Monitor
2008-10-10 23:01:01.898 adding: mythBox as a client (events: 0)
2008-10-10 23:01:01.899 MainServer::HandleAnnounce Monitor
2008-10-10 23:01:01.900 adding: mythBox as a client (events: 1)
2008-10-10 23:01:04.025 RingBuf(/mythtv/disk2/recordings/1003_20081010220000.mpg): Waited 2.0 seconds for data to become available...
2008-10-10 23:01:04.368 AFD: Opened codec 0xb4b14340, id(MPEG2VIDEO) type(Video)
2008-10-10 23:01:04.369 AFD: codec MP2 has 2 channels
2008-10-10 23:01:04.371 AFD: Opened codec 0xb4b146b0, id(MP2) type(Audio)
2008-10-10 23:02:21.787 MainServer::HandleAnnounce Playback
2008-10-10 23:02:21.791 adding: testMyth as a client (events: 0)
2008-10-10 23:02:21.793 MainServer::HandleAnnounce FileTransfer
2008-10-10 23:02:21.794 adding: testMyth as a remote file transfer
2008-10-10 23:02:25.589 MainServer::HandleAnnounce Playback
2008-10-10 23:02:25.590 adding: testMyth as a client (events: 0)
2008-10-10 23:02:25.592 MainServer::HandleAnnounce FileTransfer
2008-10-10 23:02:25.593 adding: testMyth as a remote file transfer
2008-10-10 23:02:30.087 MainServer::HandleAnnounce Playback
2008-10-10 23:02:30.105 adding: testMyth as a client (events: 0)
2008-10-10 23:02:30.107 MainServer::HandleAnnounce FileTransfer
2008-10-10 23:02:30.108 adding: testMyth as a remote file transfer
2008-10-10 23:02:33.919 MainServer::HandleAnnounce Playback
2008-10-10 23:02:33.920 adding: testMyth as a client (events: 0)
2008-10-10 23:02:33.922 MainServer::HandleAnnounce FileTransfer
2008-10-10 23:02:33.923 adding: testMyth as a remote file transfer
2008-10-10 23:02:37.407 MainServer::HandleAnnounce Playback
2008-10-10 23:02:37.409 adding: testMyth as a client (events: 0)
2008-10-10 23:02:37.410 MainServer::HandleAnnounce FileTransfer
2008-10-10 23:02:37.411 adding: testMyth as a remote file transfer
2008-10-10 23:02:40.549 MainServer::HandleAnnounce Playback
2008-10-10 23:02:40.551 adding: testMyth as a client (events: 0)
2008-10-10 23:02:40.553 MainServer::HandleAnnounce FileTransfer
2008-10-10 23:02:40.553 adding: testMyth as a remote file transfer
2008-10-10 23:02:42.799 MainServer::HandleAnnounce Playback
2008-10-10 23:02:42.800 adding: testMyth as a client (events: 0)
2008-10-10 23:02:42.802 MainServer::HandleAnnounce FileTransfer
2008-10-10 23:02:42.803 adding: testMyth as a remote file transfer
2008-10-10 23:02:48.871 MainServer::HandleAnnounce Playback
2008-10-10 23:02:48.872 adding: testMyth as a client (events: 0)
2008-10-10 23:02:48.874 MainServer::HandleAnnounce FileTransfer
2008-10-10 23:02:48.875 adding: testMyth as a remote file transfer
2008-10-10 23:02:55.896 MainServer::HandleAnnounce Playback
2008-10-10 23:02:55.897 adding: testMyth as a client (events: 0)
2008-10-10 23:02:55.899 MainServer::HandleAnnounce FileTransfer
2008-10-10 23:02:55.899 adding: testMyth as a remote file transfer
2008-10-10 23:03:05.176 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2008-10-10 23:03:09.709 MainServer::HandleAnnounce Playback
2008-10-10 23:03:09.729 adding: testMyth as a client (events: 0)
2008-10-10 23:03:09.758 TVRec(1): Changing from None to WatchingLiveTV
2008-10-10 23:03:09.766 TVRec(1): HW Tuner: 1->1
2008-10-10 23:03:11.164 MPEGRec(/dev/video0) Warning: Audio sample rate 32000 Hz
                        is not supported by ivtv driver, using 48000 Hz instead.
2008-10-10 23:03:11.211 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-10-10 23:03:11.224 MainServer::HandleAnnounce Playback
2008-10-10 23:03:11.229 adding: testMyth as a client (events: 0)
2008-10-10 23:03:11.231 MainServer::HandleAnnounce FileTransfer
2008-10-10 23:03:11.232 adding: testMyth as a remote file transfer
2008-10-10 23:03:11.769 GetRecordBasename found no entry
2008-10-10 23:03:34.785 TVRec(1): Changing from WatchingLiveTV to None
2008-10-10 23:03:35.068 Finished recording WRAL-TV News at 11: channel 1003
2008-10-10 23:06:05.216 Expiring 14 MBytes for 1003 @ Fri Oct 10 23:00:00 2008 => WRAL-TV News at 11
2008-10-10 23:07:53.072 UPnpMedia: BuildMediaMap VIDEO scan starting in :/mythtv/disk1/videos:
2008-10-10 23:07:53.105 UPnpMedia: BuildMediaMap Done. Found 13 objects
2008-10-10 23:10:03.325 MainServer::HandleAnnounce Monitor
2008-10-10 23:10:03.329 adding: mythBox as a client (events: 0)
2008-10-10 23:18:05.247 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2008-10-10 23:20:03.001 MainServer::HandleAnnounce Monitor
2008-10-10 23:20:03.002 adding: mythBox as a client (events: 0)
2008-10-10 23:27:27.856 [mpeg2video @ 0xb73d9b88]ac-tex damaged at 11 5
2008-10-10 23:27:27.874 [mpeg2video @ 0xb73d9b88]Warning MVs not available
2008-10-10 23:27:29.543 Using runtime prefix = /usr, libdir = /usr/lib
2008-10-10 23:27:29.559 Empty LocalHostName.
2008-10-10 23:27:29.561 Using localhost value of mythBox
2008-10-10 23:27:29.604 New DB connection, total: 1
2008-10-10 23:27:29.623 Connected to database 'mythconverg' at host: localhost
2008-10-10 23:27:29.625 Closing DB connection named 'DBManager0'
2008-10-10 23:27:29.626 Connected to database 'mythconverg' at host: localhost
2008-10-10 23:27:29.629 New DB connection, total: 2
2008-10-10 23:27:29.630 Connected to database 'mythconverg' at host: localhost
2008-10-10 23:27:29.633 Current Schema Version: 1214
2008-10-10 23:27:32.205 AFD: Opened codec 0x829ef50, id(MPEG2VIDEO) type(Video)
2008-10-10 23:27:32.207 AFD: codec MP2 has 2 channels
2008-10-10 23:27:32.208 AFD: Opened codec 0x829f2c0, id(MP2) type(Audio)
2008-10-10 23:27:32.464 Preview: Grabbed preview '/mythtv/disk2/recordings/1003_20081010220000.mpg' 720x480@74s

```

---

### Post by ian dobson on 2008-10-11
Hi,

Try changing the default audio rate to 48000 Hz for you ivtv card.

[HTML]2008-10-10 23:03:11.164 MPEGRec(/dev/video0) Warning: Audio sample rate 32000 Hzis not supported by ivtv driver, using 48000 Hz instead.[/HTML]

If you can go the the terminal then do a :-
sudo updatedb
sudo locate mythfrontend.log

on your frontend you'll maybe find where the log file is stored.

Regards
Ian Dobson

---

### Post by newlinux on 2008-10-11
the log you showed doesn't seem to have the part where you tried to watch the Recordings (only liveTV). An easy way to get a log is to run mythfrontend from a terminal:
```

mythfrontend -l ~/mythfrontend.log

```
will do it and save a log in the home dir. I'm guessing Knoppmyth doesn't save frontend logs to a location by default.

In your backend setup, do make sure you are using IP addresses for your backend server IPs instead of localhost.

---

### Post by dcwdrum on 2008-10-12
Thanks for all of the help.  When I went to try some of the suggestions today everything was working, which makes no sense to me, but I'm not complaining.

So thanks for the help anyways, I'll consider this fixed for now :)

---

