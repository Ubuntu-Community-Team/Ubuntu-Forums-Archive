---
title: "Mythtv not getting channel listing (guide)"
date: 2007-04-12
forum: Multimedia &amp; Video
---

### Post by 65 mustang on 2007-04-12
Hi,
  Im running 6.10 and have a PVR-500 on a 1.3 Ghz machine 512 megs ram.  I currently am able to watch TV on my mythfrontend.  Although i currently have two problems.  I am not getting the channel guide populated and i have slow video while watching live TV.

I think my channels are not being populated because either im not making a connection to the site to download them or myth cannot connect to the mysql database.

The slowness if video playback i haven't researched yet.  I have a nvidia 6200le video card running the nvidia binary driver from their site.

I am following this guide:
[https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop#head-36508059052cc77029a67b0d918b32dea018e99a](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop#head-36508059052cc77029a67b0d918b32dea018e99a)

Im going after the problem of not getting channel listings first.  Here is some output.  Could you help me decipher some of these logs.

**mythbackend.log**
```
2007-04-12 18:17:59.676 Using runtime prefix = /usr
2007-04-12 18:18:01.674 New DB connection, total: 1
2007-04-12 18:18:02.253 Connected to database 'mythconverg' at host: localhost
2007-04-12 18:18:02.805 Current Schema Version: 1160
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.
2007-04-12 19:49:08.114 Using runtime prefix = /usr
2007-04-12 19:49:08.763 New DB connection, total: 1
2007-04-12 19:49:08.893 Connected to database 'mythconverg' at host: localhost
2007-04-12 19:49:08.993 Current Schema Version: 1160
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.
2007-04-12 20:29:59.590 Using runtime prefix = /usr
2007-04-12 20:30:02.091 New DB connection, total: 1
2007-04-12 20:30:02.368 Connected to database 'mythconverg' at host: localhost
2007-04-12 20:30:02.434 Current Schema Version: 1160
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.
2007-04-12 21:26:22.082 Using runtime prefix = /usr
2007-04-12 21:26:22.286 New DB connection, total: 1
2007-04-12 21:26:22.340 Connected to database 'mythconverg' at host: localhost
2007-04-12 21:26:22.360 Current Schema Version: 1160
Starting up as the master server.
2007-04-12 21:26:22.508 New DB connection, total: 2
2007-04-12 21:26:22.528 Connected to database 'mythconverg' at host: localhost
2007-04-12 21:26:22.655 EITHelper: localtime offset -5:00:00 
2007-04-12 21:26:22.750 TVRec(1) Error: Start channel from DB is empty, setting to '2' instead.
2007-04-12 21:26:22.764 New DB connection, total: 3
2007-04-12 21:26:22.777 Connected to database 'mythconverg' at host: localhost
2007-04-12 21:26:22.974 EITHelper: localtime offset -5:00:00 
2007-04-12 21:26:22.990 TVRec(2) Error: Start channel from DB is empty, setting to '2' instead.
2007-04-12 21:26:23.079 New DB scheduler connection
2007-04-12 21:26:23.104 Connected to database 'mythconverg' at host: localhost
2007-04-12 21:26:23.204 Main::Starting HttpServer
2007-04-12 21:26:23.366 Main::Registering HttpStatus Extension
2007-04-12 21:26:23.444 mythbackend version: 0.20.20060828-3 www.mythtv.org
2007-04-12 21:26:23.464 Enabled verbose msgs:  important general
2007-04-12 21:26:23.473 AutoExpire: Found 2 recorders w/max rate of 144 MiB/min
2007-04-12 21:26:23.491 AutoExpire: Required Free Space: 2.1 GB w/freq: 10 min
2007-04-12 21:26:25.141 Reschedule requested for id -1.
2007-04-12 21:26:25.340 Scheduled 0 items in 0.2 = 0.07 match + 0.12 place
2007-04-12 21:26:25.379 Seem to be woken up by USER
2007-04-12 21:30:07.604 MainServer::HandleAnnounce Monitor
2007-04-12 21:30:07.651 adding: jsmith-desktop as a client (events: 0)
2007-04-12 21:30:07.661 MainServer::HandleAnnounce Monitor
2007-04-12 21:30:07.673 adding: jsmith-desktop as a client (events: 1)
2007-04-12 21:30:08.094 MythSocket(8164138:-1): writeStringList: Error, socket went unconnected.
2007-04-12 21:34:01.844 Using runtime prefix = /usr
2007-04-12 21:34:02.154 New DB connection, total: 1
2007-04-12 21:34:02.197 Connected to database 'mythconverg' at host: localhost
2007-04-12 21:34:02.227 Current Schema Version: 1160
Starting up as the master server.
2007-04-12 21:34:02.283 New DB connection, total: 2
2007-04-12 21:34:02.298 Connected to database 'mythconverg' at host: localhost
2007-04-12 21:34:02.325 EITHelper: localtime offset -5:00:00 
2007-04-12 21:34:02.343 TVRec(1) Error: Start channel from DB is empty, setting to '2' instead.
2007-04-12 21:34:02.374 New DB connection, total: 3
2007-04-12 21:34:02.383 Connected to database 'mythconverg' at host: localhost
2007-04-12 21:34:02.476 EITHelper: localtime offset -5:00:00 
2007-04-12 21:34:02.492 TVRec(2) Error: Start channel from DB is empty, setting to '2' instead.
2007-04-12 21:34:02.553 New DB scheduler connection
2007-04-12 21:34:02.565 Connected to database 'mythconverg' at host: localhost
2007-04-12 21:34:02.587 Main::Starting HttpServer
2007-04-12 21:34:02.610 Main::Registering HttpStatus Extension
2007-04-12 21:34:02.638 mythbackend version: 0.20.20060828-3 www.mythtv.org
2007-04-12 21:34:02.662 Enabled verbose msgs:  important general
2007-04-12 21:34:02.672 AutoExpire: Found 2 recorders w/max rate of 144 MiB/min
2007-04-12 21:34:02.689 AutoExpire: Required Free Space: 2.1 GB w/freq: 10 min
2007-04-12 21:34:04.588 Reschedule requested for id -1.
2007-04-12 21:34:04.648 Scheduled 0 items in 0.1 = 0.03 match + 0.03 place
2007-04-12 21:34:04.671 Seem to be woken up by USER
2007-04-12 21:38:22.941 Using runtime prefix = /usr
2007-04-12 21:38:23.240 New DB connection, total: 1
2007-04-12 21:38:23.281 Connected to database 'mythconverg' at host: localhost
2007-04-12 21:38:23.310 Current Schema Version: 1160
Starting up as the master server.
2007-04-12 21:38:23.368 New DB connection, total: 2
2007-04-12 21:38:23.388 Connected to database 'mythconverg' at host: localhost
2007-04-12 21:38:23.431 EITHelper: localtime offset -5:00:00 
2007-04-12 21:38:23.454 TVRec(1) Error: Start channel from DB is empty, setting to '2' instead.
2007-04-12 21:38:23.478 New DB connection, total: 3
2007-04-12 21:38:23.488 Connected to database 'mythconverg' at host: localhost
2007-04-12 21:38:23.582 EITHelper: localtime offset -5:00:00 
2007-04-12 21:38:23.598 TVRec(2) Error: Start channel from DB is empty, setting to '2' instead.
2007-04-12 21:38:23.659 New DB scheduler connection
2007-04-12 21:38:23.669 Connected to database 'mythconverg' at host: localhost
2007-04-12 21:38:23.691 Main::Starting HttpServer
2007-04-12 21:38:23.718 Main::Registering HttpStatus Extension
2007-04-12 21:38:23.741 mythbackend version: 0.20.20060828-3 www.mythtv.org
2007-04-12 21:38:23.756 Enabled verbose msgs:  important general
2007-04-12 21:38:23.773 AutoExpire: Found 2 recorders w/max rate of 144 MiB/min
2007-04-12 21:38:23.787 AutoExpire: Required Free Space: 2.1 GB w/freq: 10 min
2007-04-12 21:38:25.691 Reschedule requested for id -1.
2007-04-12 21:38:25.755 Scheduled 0 items in 0.1 = 0.03 match + 0.03 place
2007-04-12 21:38:25.787 Seem to be woken up by USER
2007-04-12 21:41:29.050 MainServer::HandleAnnounce Monitor
2007-04-12 21:41:29.084 adding: jsmith-desktop as a client (events: 0)
2007-04-12 21:41:29.094 MainServer::HandleAnnounce Monitor
2007-04-12 21:41:29.126 adding: jsmith-desktop as a client (events: 1)
2007-04-12 21:41:29.137 Reloading backend settings
2007-04-12 21:41:41.033 MainServer::HandleAnnounce Playback
2007-04-12 21:41:41.061 adding: jsmith-desktop as a client (events: 0)
2007-04-12 21:41:41.157 TVRec(1): Changing from None to WatchingLiveTV
2007-04-12 21:41:41.189 TVRec(1) Error: Start channel from DB is empty, setting to '2' instead.
2007-04-12 21:41:41.247 TVRec(1): HW Tuner: 1->1
2007-04-12 21:46:00.761 Finished recording Unknown: channel 1101
2007-04-12 21:46:01.649 Finished recording Unknown: channel 1101
2007-04-12 21:46:02.410 TVRec(1): RingBufferChanged()
2007-04-12 21:46:02.507 Finished recording Unknown: channel 1101
[mpeg @ 0xb73bf500]Parser not found for Codec Id: 94210 !
0: start_time: 0.036 duration: 22.985
1: start_time: 392.959 duration: 23.015
2: start_time: 0.017 duration: 22.976
stream: start_time: 0.189 duration: 4621.744 bitrate=288 kb/s
2007-04-12 21:46:22.763 AFD: Opened codec 0x81a5c40, id(MPEG2VIDEO) type(Video)
2007-04-12 21:46:23.457 AFD: Opened codec 0x81a1370, id(MP2) type(Audio)
2007-04-12 21:46:45.893 TVRec(1): Changing from WatchingLiveTV to None
2007-04-12 21:46:46.438 Finished recording Unknown: channel 1001
2007-04-12 21:46:55.230 MainServer::HandleAnnounce Playback
2007-04-12 21:46:55.471 adding: jsmith-desktop as a client (events: 0)
2007-04-12 21:46:55.537 TVRec(1): Changing from None to WatchingLiveTV
2007-04-12 21:46:55.560 TVRec(1): HW Tuner: 1->1
2007-04-12 21:48:48.604 Expiring Unknown from Thu Apr 12 21:46:00 2007, 28 MBytes, forced expire (LiveTV recording)
2007-04-12 21:50:23.144 Finished recording Unknown: channel 1001
2007-04-12 21:50:23.376 Finished recording Unknown: channel 1001
2007-04-12 21:50:23.979 TVRec(1): RingBufferChanged()
2007-04-12 21:50:24.049 Finished recording Unknown: channel 1001
[mpeg @ 0xb73bf500]Parser not found for Codec Id: 94210 !
0: start_time: 0.036 duration: 18.459
1: start_time: 421.176 duration: 18.477
2: start_time: 0.017 duration: 18.431
stream: start_time: 0.189 duration: 4884.842 bitrate=219 kb/s
2007-04-12 21:50:29.810 AFD: Opened codec 0x823b970, id(MPEG2VIDEO) type(Video)
2007-04-12 21:50:30.373 AFD: Opened codec 0x81994c0, id(MP2) type(Audio)
2007-04-12 21:51:10.815 Finished recording Unknown: channel 1003
2007-04-12 21:51:11.456 Finished recording Unknown: channel 1003
[mpeg @ 0xb73bf500]2007-04-12 21:51:12.255 TVRec(1): RingBufferChanged()
2007-04-12 21:51:12.551 Finished recording Unknown: channel 1003
Parser not found for Codec Id: 94210 !
0: start_time: 18.523 duration: 4.162
1: start_time: 439.827 duration: 4.027
2: start_time: 18.476 duration: 4.164
stream: start_time: 205.293 duration: 4726.423 bitrate=51 kb/s
2007-04-12 21:51:15.159 AFD: Opened codec 0x82397d0, id(MPEG2VIDEO) type(Video)
2007-04-12 21:51:22.247 AFD: Opened codec 0x81c1fe0, id(MP2) type(Audio)
2007-04-12 21:52:50.886 Expiring Unknown from Thu Apr 12 21:50:23 2007, 29 MBytes, forced expire (LiveTV recording)
2007-04-12 21:53:08.031 TVRec(1): Changing from WatchingLiveTV to None
2007-04-12 21:53:08.479 Finished recording Unknown: channel 1005
2007-04-12 21:54:51.111 Expiring Unknown from Thu Apr 12 21:51:11 2007, 73 MBytes, forced expire (LiveTV recording)
```

**sudo mythfilldatabase > output.txt**
```
2007-04-12 22:24:59.211 Using runtime prefix = /usr
2007-04-12 22:24:59.282 New DB connection, total: 1
2007-04-12 22:24:59.293 Connected to database 'mythconverg' at host: localhost
2007-04-12 22:24:59.322 New DB connection, total: 2
2007-04-12 22:24:59.323 Connected to database 'mythconverg' at host: localhost
2007-04-12 22:24:59.324 Updating source #1 (PVR-500_0) with grabber datadirect
2007-04-12 22:24: 59.326
2007-04-12 22:24:59.326 Checking day @ offset 0, date: Thu Apr 12 2007
2007-04-12 22:24:59.331 Data refresh needed because no data exists for day @ offset 0 from 6PM - midnight.
2007-04-12 22:24:59.331 Refreshing data for Thu Apr 12 2007
2007-04-12 22:24:59.334 New DB DataDirect connection
2007-04-12 22:24:59.335 Connected to database 'mythconverg' at host: localhost
2007-04-12 22:24:59.337 Retrieving datadirect data.
2007-04-12 22:24: 59.338 Grabbing data for Thu Apr 12 2007 offset 0
2007-04-12 22:24:59.338 From Thu Apr 12 05:00:00 2007 to Fri Apr 13 05:00:00 2007 (UTC)
2007-04-12 22:24:59.338 Grabbing listing data
2007-04-12 22:25:00.232 Grab complete.  Actual data from  to  (UTC)
2007-04-12 22:25:00.233 Main temp tables populated.
2007-04-12 22:25:00.234 Updating myth channels.
2007-04-12 22:25:00.238 New DB connection, total: 3
2007-04-12 22:25:00.239 Connected to database 'mythconverg' at host: localhost
2007-04-12 22:25:00.242 Updating icons for sourceid: 1
2007-04-12 22:25:00.246 Channels updated.
2007-04-12 22:25:00.250 Did not find any new program data.
2007-04-12 22:25:00.251
2007-04-12 22:25:00.251 Checking day @ offset 1, date: Fri Apr 13 2007
2007-04-12 22:25:00.251 Refreshing data for Fri Apr 13 2007
2007-04-12 22:25:00.252 Retrieving datadirect data.
2007-04-12 22:25:00.252 Grabbing data for Thu Apr 12 2007 offset 1
2007-04-12 22:25:00.252 From Fri Apr 13 05:00:00 2007 to Sat Apr 14 05:00:00 2007 (UTC)
2007-04-12 22:25:00.253 Grabbing listing data
2007-04-12 22:25:00.849 Grab complete.  Actual data from  to  (UTC)
2007-04-12 22:25:00.850 Main temp tables populated.
2007-04-12 22:25:00.854 Did not find any new program data.
2007-04-12 22:25:00.854
2007-04-12 22:25:00.854 Checking day @ offset 2, date: Sat Apr 14 2007
2007-04-12 22:25:00.915 Data refresh needed because no data exists for day @ offset 2 from 6PM - midnight.
2007-04-12 22:25: 00.916 Refreshing data for Sat Apr 14 2007
2007-04-12 22:25:00.917 Retrieving datadirect data.
2007-04-12 22:25:00.917 Grabbing data for Thu Apr 12 2007 offset 2
2007-04-12 22:25:00.917 From Sat Apr 14 05:00:00 2007 to Sun Apr 15 05:00:00 2007 (UTC)
2007-04-12 22:25:00.917 Grabbing listing data
2007-04-12 22:25:02.026 Grab complete.  Actual data from  to  (UTC)
2007-04-12 22:25:02.027 Main temp tables populated.
2007-04-12 22:25:02.031 Did not find any new program data.
2007-04-12 22:25:02.031
2007-04-12 22:25:02.031 Checking day @ offset 3, date: Sun Apr 15 2007
2007-04-12 22:25:02.036 Data refresh needed because no data exists for day @ offset 3 from 6PM - midnight.
2007-04-12 22:25: 02.036 Refreshing data for Sun Apr 15 2007
2007-04-12 22:25:02.065 Retrieving datadirect data.
2007-04-12 22:25:02.066 Grabbing data for Thu Apr 12 2007 offset 3
2007-04-12 22:25:02.066 From Sun Apr 15 05:00:00 2007 to Mon Apr 16 05:00:00 2007 (UTC)
2007-04-12 22:25:02.066 Grabbing listing data
2007-04-12 22:25:02.974 Grab complete.  Actual data from  to  (UTC)
2007-04-12 22:25:02.975 Main temp tables populated.
2007-04-12 22:25:02.979 Did not find any new program data.
2007-04-12 22:25:02.979
2007-04-12 22:25:02.979 Checking day @ offset 4, date: Mon Apr 16 2007
2007-04-12 22:25:02.984 Data refresh needed because no data exists for day @ offset 4 from 6PM - midnight.
2007-04-12 22:25: 02.984 Refreshing data for Mon Apr 16 2007
2007-04-12 22:25:03.049 Retrieving datadirect data.
2007-04-12 22:25:03.049 Grabbing data for Thu Apr 12 2007 offset 4
2007-04-12 22:25:03.049 From Mon Apr 16 05:00:00 2007 to Tue Apr 17 05:00:00 2007 (UTC)
2007-04-12 22:25:03.049 Grabbing listing data
2007-04-12 22:25:03.894 Grab complete.  Actual data from  to  (UTC)
2007-04-12 22:25:03.895 Main temp tables populated.
2007-04-12 22:25:03.899 Did not find any new program data.
2007-04-12 22:25:03.900
2007-04-12 22:25:03.900 Checking day @ offset 5, date: Tue Apr 17 2007
2007-04-12 22:25:03.904 Data refresh needed because no data exists for day @ offset 5 from 6PM - midnight.
2007-04-12 22:25: 03.904 Refreshing data for Tue Apr 17 2007
2007-04-12 22:25:03.950 Retrieving datadirect data.
2007-04-12 22:25:03.950 Grabbing data for Thu Apr 12 2007 offset 5
2007-04-12 22:25:03.950 From Tue Apr 17 05:00:00 2007 to Wed Apr 18 05:00:00 2007 (UTC)
2007-04-12 22:25:03.950 Grabbing listing data
2007-04-12 22:25:05.011 Grab complete.  Actual data from  to  (UTC)
2007-04-12 22:25:05.012 Main temp tables populated.
2007-04-12 22:25:05.016 Did not find any new program data.
2007-04-12 22:25:05.017
2007-04-12 22:25:05.017 Checking day @ offset 6, date: Wed Apr 18 2007
2007-04-12 22:25:05.084 Data refresh needed because no data exists for day @ offset 6 from 6PM - midnight.
2007-04-12 22:25: 05.084 Refreshing data for Wed Apr 18 2007
2007-04-12 22:25:05.085 Retrieving datadirect data.
2007-04-12 22:25:05.086 Grabbing data for Thu Apr 12 2007 offset 6
2007-04-12 22:25:05.086 From Wed Apr 18 05:00:00 2007 to Thu Apr 19 05:00:00 2007 (UTC)
2007-04-12 22:25:05.086 Grabbing listing data
2007-04-12 22:25:06.064 Grab complete.  Actual data from  to  (UTC)
2007-04-12 22:25:06.065 Main temp tables populated.
2007-04-12 22:25:06.070 Did not find any new program data.
2007-04-12 22:25:06.070
2007-04-12 22:25:06.070 Checking day @ offset 7, date: Thu Apr 19 2007
2007-04-12 22:25:06.131 Data refresh needed because no data exists for day @ offset 7 from 6PM - midnight.
2007-04-12 22:25: 06.132 Refreshing data for Thu Apr 19 2007
2007-04-12 22:25:06.133 Retrieving datadirect data.
2007-04-12 22:25:06.133 Grabbing data for Thu Apr 12 2007 offset 7
2007-04-12 22:25:06.133 From Thu Apr 19 05:00:00 2007 to Fri Apr 20 05:00:00 2007 (UTC)
2007-04-12 22:25:06.133 Grabbing listing data
2007-04-12 22:25:07.151 Grab complete.  Actual data from  to  (UTC)
2007-04-12 22:25:07.153 Main temp tables populated.
2007-04-12 22:25:07.192 Did not find any new program data.
2007-04-12 22:25:07.193
2007-04-12 22:25:07.193 Checking day @ offset 8, date: Fri Apr 20 2007
2007-04-12 22:25:07.197 Data refresh needed because no data exists for day @ offset 8 from 6PM - midnight.
2007-04-12 22:25: 07.198 Refreshing data for Fri Apr 20 2007
2007-04-12 22:25:07.198 Retrieving datadirect data.
2007-04-12 22:25:07.199 Grabbing data for Thu Apr 12 2007 offset 8
2007-04-12 22:25:07.199 From Fri Apr 20 05:00:00 2007 to Sat Apr 21 05:00:00 2007 (UTC)
2007-04-12 22:25:07.199 Grabbing listing data
2007-04-12 22:25:07.583 Grab complete.  Actual data from  to  (UTC)
2007-04-12 22:25:07.585 Main temp tables populated.
2007-04-12 22:25:07.589 Did not find any new program data.
2007-04-12 22:25:07.590
2007-04-12 22:25:07.590 Checking day @ offset 9, date: Sat Apr 21 2007
2007-04-12 22:25:07.637 Data refresh needed because no data exists for day @ offset 9 from 6PM - midnight.
2007-04-12 22:25: 07.638 Refreshing data for Sat Apr 21 2007
2007-04-12 22:25:07.639 Retrieving datadirect data.
2007-04-12 22:25:07.639 Grabbing data for Thu Apr 12 2007 offset 9
2007-04-12 22:25:07.639 From Sat Apr 21 05:00:00 2007 to Sun Apr 22 05:00:00 2007 (UTC)
2007-04-12 22:25:07.639 Grabbing listing data
2007-04-12 22:25:08.004 Grab complete.  Actual data from  to  (UTC)
2007-04-12 22:25:08.006 Main temp tables populated.
2007-04-12 22:25:08.075 Did not find any new program data.
2007-04-12 22:25:08.075
2007-04-12 22:25:08.076 Checking day @ offset 10, date: Sun Apr 22 2007
2007-04-12 22:25:08.080 Data refresh needed because no data exists for day @ offset 10 from 6PM - midnight.
2007-04-12 22:25: 08.080 Refreshing data for Sun Apr 22 2007
2007-04-12 22:25:08.081 Retrieving datadirect data.
2007-04-12 22:25:08.082 Grabbing data for Thu Apr 12 2007 offset 10
2007-04-12 22:25:08.082 From Sun Apr 22 05:00:00 2007 to Mon Apr 23 05:00:00 2007 (UTC)
2007-04-12 22:25:08.082 Grabbing listing data
2007-04-12 22:25:08.399 Grab complete.  Actual data from  to  (UTC)
2007-04-12 22:25:08.402 Main temp tables populated.
2007-04-12 22:25:08.406 Did not find any new program data.
2007-04-12 22:25:08.406
2007-04-12 22:25:08.407 Checking day @ offset 11, date: Mon Apr 23 2007
2007-04-12 22:25:08.476 Data refresh needed because no data exists for day @ offset 11 from 6PM - midnight.
2007-04-12 22:25: 08.477 Refreshing data for Mon Apr 23 2007
2007-04-12 22:25:08.478 Retrieving datadirect data.
2007-04-12 22:25:08.478 Grabbing data for Thu Apr 12 2007 offset 11
2007-04-12 22:25:08.478 From Mon Apr 23 05:00:00 2007 to Tue Apr 24 05:00:00 2007 (UTC)
2007-04-12 22:25:08.478 Grabbing listing data
2007-04-12 22:25:09.056 Grab complete.  Actual data from  to  (UTC)
2007-04-12 22:25:09.059 Main temp tables populated.
2007-04-12 22:25:09.064 Did not find any new program data.
2007-04-12 22:25:09.064
2007-04-12 22:25:09.064 Checking day @ offset 12, date: Tue Apr 24 2007
2007-04-12 22:25:09.070 Data refresh needed because no data exists for day @ offset 12 from 6PM - midnight.
2007-04-12 22:25: 09.070 Refreshing data for Tue Apr 24 2007
2007-04-12 22:25:09.071 Retrieving datadirect data.
2007-04-12 22:25:09.071 Grabbing data for Thu Apr 12 2007 offset 12
2007-04-12 22:25:09.071 From Tue Apr 24 05:00:00 2007 to Wed Apr 25 05:00:00 2007 (UTC)
2007-04-12 22:25:09.072 Grabbing listing data
2007-04-12 22:25:10.182 Grab complete.  Actual data from  to  (UTC)
2007-04-12 22:25:10.183 Main temp tables populated.
2007-04-12 22:25:10.188 Did not find any new program data.
2007-04-12 22:25:10.188
2007-04-12 22:25:10.188 Checking day @ offset 13, date: Wed Apr 25 2007
2007-04-12 22:25:10.228 Data refresh needed because no data exists for day @ offset 13 from 6PM - midnight.
2007-04-12 22:25: 10.229 Refreshing data for Wed Apr 25 2007
2007-04-12 22:25:10.243 Retrieving datadirect data.
2007-04-12 22:25:10.243 Grabbing data for Thu Apr 12 2007 offset 13
2007-04-12 22:25:10.243 From Wed Apr 25 05:00:00 2007 to Thu Apr 26 05:00:00 2007 (UTC)
2007-04-12 22:25:10.244 Grabbing listing data
2007-04-12 22:25:11.212 Grab complete.  Actual data from  to  (UTC)
2007-04-12 22:25:11.214 Main temp tables populated.
2007-04-12 22:25:11.218 Did not find any new program data.
2007-04-12 22:25:11.218 Updating source #2 (PVR-500_1) with grabber datadirect
2007-04-12 22:25:11.218
2007-04-12 22:25:11.218 Checking day @ offset 0, date: Thu Apr 12 2007
2007-04-12 22:25:11.223 Data refresh needed because no data exists for day @ offset 0 from 6PM - midnight.
2007-04-12 22:25:11.223 Refreshing data for Thu Apr 12 2007
2007-04-12 22:25:11.224 Retrieving datadirect data.
2007-04-12 22:25:11.224 Grabbing data for Thu Apr 12 2007 offset 0
2007-04-12 22:25:11.225 From Thu Apr 12 05:00:00 2007 to Fri Apr 13 05:00:00 2007 (UTC)
2007-04-12 22:25:11.226 Grabbing listing data
2007-04-12 22:25:11.951 Grab complete.  Actual data from  to  (UTC)
2007-04-12 22:25:11.952 Main temp tables populated.
2007-04-12 22:25:11.952 Updating myth channels.
2007-04-12 22:25:11.956 Updating icons for sourceid: 2
2007-04-12 22:25:11.959 Channels updated.
2007-04-12 22:25:12.006 Did not find any new program data.
2007-04-12 22:25:12.007
2007-04-12 22:25:12.007 Checking day @ offset 1, date: Fri Apr 13 2007
2007-04-12 22:25:12.007 Refreshing data for Fri Apr 13 2007
2007-04-12 22:25:12.008 Retrieving datadirect data.
2007-04-12 22:25:12.008 Grabbing data for Thu Apr 12 2007 offset 1
2007-04-12 22:25:12.008 From Fri Apr 13 05:00:00 2007 to Sat Apr 14 05:00:00 2007 (UTC)
2007-04-12 22:25:12.008 Grabbing listing data
2007-04-12 22:25:13.342 Grab complete.  Actual data from  to  (UTC)
2007-04-12 22:25:13.343 Main temp tables populated.
2007-04-12 22:25:13.348 Did not find any new program data.
2007-04-12 22:25:13.348
2007-04-12 22:25:13.348 Checking day @ offset 2, date: Sat Apr 14 2007
2007-04-12 22:25:13.352 Data refresh needed because no data exists for day @ offset 2 from 6PM - midnight.
2007-04-12 22:25: 13.353 Refreshing data for Sat Apr 14 2007
2007-04-12 22:25:13.422 Retrieving datadirect data.
2007-04-12 22:25:13.422 Grabbing data for Thu Apr 12 2007 offset 2
2007-04-12 22:25:13.422 From Sat Apr 14 05:00:00 2007 to Sun Apr 15 05:00:00 2007 (UTC)
2007-04-12 22:25:13.423 Grabbing listing data
2007-04-12 22:25:14.252 Grab complete.  Actual data from  to  (UTC)
2007-04-12 22:25:14.254 Main temp tables populated.
2007-04-12 22:25:14.258 Did not find any new program data.
2007-04-12 22:25:14.258
2007-04-12 22:25:14.258 Checking day @ offset 3, date: Sun Apr 15 2007
2007-04-12 22:25:14.263 Data refresh needed because no data exists for day @ offset 3 from 6PM - midnight.
2007-04-12 22:25: 14.263 Refreshing data for Sun Apr 15 2007
2007-04-12 22:25:14.264 Retrieving datadirect data.
2007-04-12 22:25:14.264 Grabbing data for Thu Apr 12 2007 offset 3
2007-04-12 22:25:14.264 From Sun Apr 15 05:00:00 2007 to Mon Apr 16 05:00:00 2007 (UTC)
2007-04-12 22:25:14.265 Grabbing listing data
2007-04-12 22:25:14.990 Grab complete.  Actual data from  to  (UTC)
2007-04-12 22:25:14.991 Main temp tables populated.
2007-04-12 22:25:14.995 Did not find any new program data.
2007-04-12 22:25:14.995
2007-04-12 22:25:14.995 Checking day @ offset 4, date: Mon Apr 16 2007
2007-04-12 22:25:15.000 Data refresh needed because no data exists for day @ offset 4 from 6PM - midnight.
2007-04-12 22:25: 15.000 Refreshing data for Mon Apr 16 2007
2007-04-12 22:25:15.002 Retrieving datadirect data.
2007-04-12 22:25:15.002 Grabbing data for Thu Apr 12 2007 offset 4
2007-04-12 22:25:15.002 From Mon Apr 16 05:00:00 2007 to Tue Apr 17 05:00:00 2007 (UTC)
2007-04-12 22:25:15.003 Grabbing listing data
2007-04-12 22:25:16.044 Grab complete.  Actual data from  to  (UTC)
2007-04-12 22:25:16.045 Main temp tables populated.
2007-04-12 22:25:16.050 Did not find any new program data.
2007-04-12 22:25:16.050
2007-04-12 22:25:16.050 Checking day @ offset 5, date: Tue Apr 17 2007
2007-04-12 22:25:16.111 Data refresh needed because no data exists for day @ offset 5 from 6PM - midnight.
2007-04-12 22:25: 16.111 Refreshing data for Tue Apr 17 2007
2007-04-12 22:25:16.112 Retrieving datadirect data.
2007-04-12 22:25:16.112 Grabbing data for Thu Apr 12 2007 offset 5
2007-04-12 22:25:16.113 From Tue Apr 17 05:00:00 2007 to Wed Apr 18 05:00:00 2007 (UTC)
2007-04-12 22:25:16.113 Grabbing listing data
2007-04-12 22:25:17.109 Grab complete.  Actual data from  to  (UTC)
2007-04-12 22:25:17.110 Main temp tables populated.
2007-04-12 22:25:17.114 Did not find any new program data.
2007-04-12 22:25:17.114
2007-04-12 22:25:17.114 Checking day @ offset 6, date: Wed Apr 18 2007
2007-04-12 22:25:17.153 Data refresh needed because no data exists for day @ offset 6 from 6PM - midnight.
2007-04-12 22:25: 17.154 Refreshing data for Wed Apr 18 2007
2007-04-12 22:25:17.161 Retrieving datadirect data.
2007-04-12 22:25:17.162 Grabbing data for Thu Apr 12 2007 offset 6
2007-04-12 22:25:17.162 From Wed Apr 18 05:00:00 2007 to Thu Apr 19 05:00:00 2007 (UTC)
2007-04-12 22:25:17.162 Grabbing listing data
2007-04-12 22:25:18.246 Grab complete.  Actual data from  to  (UTC)
2007-04-12 22:25:18.248 Main temp tables populated.
2007-04-12 22:25:18.252 Did not find any new program data.
2007-04-12 22:25:18.253
2007-04-12 22:25:18.253 Checking day @ offset 7, date: Thu Apr 19 2007
2007-04-12 22:25:18.314 Data refresh needed because no data exists for day @ offset 7 from 6PM - midnight.
2007-04-12 22:25: 18.314 Refreshing data for Thu Apr 19 2007
2007-04-12 22:25:18.315 Retrieving datadirect data.
2007-04-12 22:25:18.315 Grabbing data for Thu Apr 12 2007 offset 7
2007-04-12 22:25:18.316 From Thu Apr 19 05:00:00 2007 to Fri Apr 20 05:00:00 2007 (UTC)
2007-04-12 22:25:18.316 Grabbing listing data
2007-04-12 22:25:19.420 Grab complete.  Actual data from  to  (UTC)
2007-04-12 22:25:19.421 Main temp tables populated.
2007-04-12 22:25:19.448 Did not find any new program data.
2007-04-12 22:25:19.449
2007-04-12 22:25:19.449 Checking day @ offset 8, date: Fri Apr 20 2007
2007-04-12 22:25:19.454 Data refresh needed because no data exists for day @ offset 8 from 6PM - midnight.
2007-04-12 22:25: 19.454 Refreshing data for Fri Apr 20 2007
2007-04-12 22:25:19.455 Retrieving datadirect data.
2007-04-12 22:25:19.455 Grabbing data for Thu Apr 12 2007 offset 8
2007-04-12 22:25:19.455 From Fri Apr 20 05:00:00 2007 to Sat Apr 21 05:00:00 2007 (UTC)
2007-04-12 22:25:19.456 Grabbing listing data
2007-04-12 22:25:20.601 Grab complete.  Actual data from  to  (UTC)
2007-04-12 22:25:20.602 Main temp tables populated.
2007-04-12 22:25:20.606 Did not find any new program data.
2007-04-12 22:25:20.606
2007-04-12 22:25:20.607 Checking day @ offset 9, date: Sat Apr 21 2007
2007-04-12 22:25:20.675 Data refresh needed because no data exists for day @ offset 9 from 6PM - midnight.
2007-04-12 22:25: 20.676 Refreshing data for Sat Apr 21 2007
2007-04-12 22:25:20.677 Retrieving datadirect data.
2007-04-12 22:25:20.677 Grabbing data for Thu Apr 12 2007 offset 9
2007-04-12 22:25:20.677 From Sat Apr 21 05:00:00 2007 to Sun Apr 22 05:00:00 2007 (UTC)
2007-04-12 22:25:20.678 Grabbing listing data
2007-04-12 22:25:21.697 Grab complete.  Actual data from  to  (UTC)
2007-04-12 22:25:21.698 Main temp tables populated.
2007-04-12 22:25:21.703 Did not find any new program data.
2007-04-12 22:25:21.703
2007-04-12 22:25:21.703 Checking day @ offset 10, date: Sun Apr 22 2007
2007-04-12 22:25:21.762 Data refresh needed because no data exists for day @ offset 10 from 6PM - midnight.
2007-04-12 22:25: 21.763 Refreshing data for Sun Apr 22 2007
2007-04-12 22:25:21.764 Retrieving datadirect data.
2007-04-12 22:25:21.764 Grabbing data for Thu Apr 12 2007 offset 10
2007-04-12 22:25:21.764 From Sun Apr 22 05:00:00 2007 to Mon Apr 23 05:00:00 2007 (UTC)
2007-04-12 22:25:21.765 Grabbing listing data
2007-04-12 22:25:22.854 Grab complete.  Actual data from  to  (UTC)
2007-04-12 22:25:22.855 Main temp tables populated.
2007-04-12 22:25:22.875 Did not find any new program data.
2007-04-12 22:25:22.875
2007-04-12 22:25:22.875 Checking day @ offset 11, date: Mon Apr 23 2007
2007-04-12 22:25:22.889 Data refresh needed because no data exists for day @ offset 11 from 6PM - midnight.
2007-04-12 22:25: 22.889 Refreshing data for Mon Apr 23 2007
2007-04-12 22:25:22.890 Retrieving datadirect data.
2007-04-12 22:25:22.891 Grabbing data for Thu Apr 12 2007 offset 11
2007-04-12 22:25:22.891 From Mon Apr 23 05:00:00 2007 to Tue Apr 24 05:00:00 2007 (UTC)
2007-04-12 22:25:22.891 Grabbing listing data
2007-04-12 22:25:23.992 Grab complete.  Actual data from  to  (UTC)
2007-04-12 22:25:23.996 Main temp tables populated.
2007-04-12 22:25:24.000 Did not find any new program data.
2007-04-12 22:25:24.001
2007-04-12 22:25:24.001 Checking day @ offset 12, date: Tue Apr 24 2007
2007-04-12 22:25:24.006 Data refresh needed because no data exists for day @ offset 12 from 6PM - midnight.
2007-04-12 22:25: 24.007 Refreshing data for Tue Apr 24 2007
2007-04-12 22:25:24.008 Retrieving datadirect data.
2007-04-12 22:25:24.008 Grabbing data for Thu Apr 12 2007 offset 12
2007-04-12 22:25:24.008 From Tue Apr 24 05:00:00 2007 to Wed Apr 25 05:00:00 2007 (UTC)
2007-04-12 22:25:24.008 Grabbing listing data
2007-04-12 22:25:25.147 Grab complete.  Actual data from  to  (UTC)
2007-04-12 22:25:25.148 Main temp tables populated.
2007-04-12 22:25:25.153 Did not find any new program data.
2007-04-12 22:25:25.153
2007-04-12 22:25:25.153 Checking day @ offset 13, date: Wed Apr 25 2007
2007-04-12 22:25:25.193 Data refresh needed because no data exists for day @ offset 13 from 6PM - midnight.
2007-04-12 22:25: 25.194 Refreshing data for Wed Apr 25 2007
2007-04-12 22:25:25.195 Retrieving datadirect data.
2007-04-12 22:25:25.195 Grabbing data for Thu Apr 12 2007 offset 13
2007-04-12 22:25:25.195 From Wed Apr 25 05:00:00 2007 to Thu Apr 26 05:00:00 2007 (UTC)
2007-04-12 22:25:25.195 Grabbing listing data
2007-04-12 22:25:25.770 Grab complete.  Actual data from  to  (UTC)
2007-04-12 22:25:25.772 Main temp tables populated.
2007-04-12 22:25:25.776 Did not find any new program data.
2007-04-12 22:25:25.839 New DB connection, total: 4
2007-04-12 22:25:25.840 Connected to database 'mythconverg' at host: localhost
2007-04-12 22:25:25.843 New DB connection, total: 5
2007-04-12 22:25: 25.844 Connected to database 'mythconverg' at host: localhost
2007-04-12 22:25:25.848 Failed to fetch some program info
2007-04-12 22:25:25.849 Adjusting program database end times.
2007-04-12 22:25:25.849      0 replacements made
2007-04-12 22:25:25.849 Marking generic episodes.
2007-04-12 22:25:25.850     Found 0
2007-04-12 22:25:25.851 Marking repeats.
2007-04-12 22:25:25.854     Found 0
2007-04-12 22:25:25.854 Unmarking new episode rebroadcast repeats.
2007-04-12 22:25:25.855     Found 0
2007-04-12 22:25:25.855 Marking episode first showings.
2007-04-12 22:25:25.856     Found 0
2007-04-12 22:25:25.856 Marking episode last showings.
2007-04-12 22:25:25.856     Found 0
2007-04-12 22:25:25.860 Grabbing next suggested grabbing time
2007-04-12 22:25:26.922 DataDirect: BlockedTime is: 2007-04-12T22:25:26
2007-04-12 22:25:26.924 DataDirect: NextSuggestedTime is: 2007-04-13T00:13:20
2007-04-12 22:25:26.931
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2007-04-12 22:25:26.942 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2007-04-12 22:25:26.944 Connection timed out.          
            You probably should modify the Master Server
            settings in the setup program and set the    
            proper IP address.
2007-04-12 22:25:26.944 Error rescheduling id -1 in ScheduledRecording::signalChange
2007-04-12 22:25:26.945 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2007-04-12 22:25: 26.945 Connection timed out.          
            You probably should modify the Master Server
            settings in the setup program and set the    
            proper IP address.
2007-04-12 22:25:26.949 mythfilldatabase run complete.
```

---

### Post by 65 mustang on 2007-04-13
**mythtvfrontend**
```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
2007-04-12 23:19:37.339 Using runtime prefix = /usr
2007-04-12 23:19:37.562 Gnome-Screensaver support enabled
2007-04-12 23:19: 37.563 DPMS is active.
2007-04-12 23:19:37.753 New DB connection, total: 1
2007-04-12 23:19:37.792 Connected to database 'mythconverg' at host: localhost
2007-04-12 23:19:37.797 Total desktop dim: 1280x1024, with 1 screen[s].
2007-04-12 23:19:37.811 Using screen 0, 1280x1024 at 0,0
2007-04-12 23:19:37.852 Current Schema Version: 1160
2007-04-12 23:19:37.852 mythfrontend version: 0.20.20060828-3 www.mythtv.org
2007-04-12 23:19:37.853 Enabled verbose msgs:  important general
2007-04-12 23:19:38.661 Total desktop dim: 1280x1024, with 1 screen[s].
2007-04-12 23:19:38.664 Using screen 0, 1280x1024 at 0,0
2007-04-12 23:19: 38.666 Switching to square mode (G.A.N.T.)
2007-04-12 23:19:38.826 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2007-04-12 23:19:40.152 Joystick disabled.
2007-04-12 23:19:41.022 Loading from: /usr/share/mythtv/themes/G.A.N.T./base.xml
2007-04-12 23:19:41.285 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-04-12 23:19: 41.397 Registering Internal as a media playback plugin.
2007-04-12 23:19:55.137 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2007-04-12 23:19:55.139 Using protocol version 31 
```

---

### Post by majoridiot on 2007-04-13
it doesn't look like you have the grabber setup correctly.  

yours:
> 2007-04-12 22:25:00.854 Checking day @ offset 2, date: Sat Apr 14 2007
2007-04-12 22:25:00.915 Data refresh needed because no data exists for day @ offset 2 from 6PM - midnight.
2007-04-12 22:25: 00.916 Refreshing data for Sat Apr 14 2007
2007-04-12 22:25:00.917 Retrieving datadirect data.
2007-04-12 22:25:00.917 Grabbing data for Thu Apr 12 2007 offset 2
2007-04-12 22:25:00.917 From Sat Apr 14 05:00:00 2007 to Sun Apr 15 05:00:00 2007 (UTC)
2007-04-12 22:25:00.917 Grabbing listing data
2007-04-12 22:25:02.026 Grab complete.  Actual data from  to  (UTC)
2007-04-12 22:25:02.027 Main temp tables populated.
2007-04-12 22:25:02.031 Did not find any new program data.
2007-04-12 22:25:02.031

from a good grab:
> 2007-04-13 01:35:55.234 Checking day @ offset 1, date: Sat Apr 14 2007
2007-04-13 01:35:55.234 Refreshing data for Sat Apr 14 2007
2007-04-13 01:35:55.250 New DB DataDirect connection
2007-04-13 01:35:55.251 Connected to database 'mythconverg' at host: localhost
2007-04-13 01:35:55.267 Retrieving datadirect data.
2007-04-13 01:35:55.268 Grabbing data for Fri Apr 13 2007 offset 1
2007-04-13 01:35:55.268 From Sat Apr 14 05:00:00 2007 to Sun Apr 15 05:00:00 2007 (UTC)
2007-04-13 01:35:55.268 Grabbing listing data
--01:35:55--  [http://datadirect.webservices.zap2it.com/tvlistings/xtvdService](http://datadirect.webservices.zap2it.com/tvlistings/xtvdService)
           => `-'
Resolving datadirect.webservices.zap2it.com... 206.18.98.160
Connecting to datadirect.webservices.zap2it.com|206.18.98.160|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to datadirect.webservices.zap2it.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

if you are using datadirect, you need to go here: [http://labs.zap2it.com/](http://labs.zap2it.com/) 
and setup an account with the channels you want.  use the mythtv project code ZIYN-DQZO-SBUT

once you have your channel profile setup, run mythtv-setup  and go to 3. sources, enter the user
id and password you just set up @ zap2it and hit the "retrieve lineups button"

then exit from setup and run mythfilldatabase again

---

