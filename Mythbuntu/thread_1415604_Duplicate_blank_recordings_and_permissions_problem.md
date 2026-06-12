---
title: "Duplicate blank recordings and permissions problems on mythbuntu 9.10"
date: 2010-02-25
forum: Mythbuntu
---

### Post by teet on 2010-02-25
I installed a ubuntu 9.10 on my parent's HTPC several months ago.  Their old hdd crashed so I installed a fresh copy of ubuntu on a new hdd and added in all the mythbuntu goodness.  Everything was going great up until a few months ago whenever I started noticing that mythtv was randomly generating duplicate blank recordings.  Whenever I logged into mythweb there would be the regular recording (which played just fine) and a second one with a filesize of "B" (blank???) that was empty.  This was annoying, but at least myth was still recording.  I checked on the file permissions of my recordings and noticed that some of the files had been recorded under the "alex" user instead of the "mythtv" user, and furthermore the permissions were different.  I chown'ed and chgrp'ed and chmod 775'ed all the files and directories and everything was all good.

However, myth would still sometimes randomly generate duplicate blank recordings.  Sometimes rebooting would fix the problem...sometimes not.  In the past several days, myth has again been generating blank recordings, but now it sometimes doesn't even record the show.  I again checked the permissions and ownership and found that files were once again being recorded under the "alex" user.  I think this is the root of the problem.  How do you make mythtv only record stuff under the "mythtv" user and use appropriate permission?

Below is a snippet from my mythbackend.log.  The tuner was supposed to record the young and the restless (for my mom).

```

2010-02-24 10:57:00.470 Scheduled 130 items in 0.4 = 0.06 match + 0.38 place
2010-02-24 10:59:30.410 TVRec(1): ASK_RECORDING 1 29 0 0
2010-02-24 11:00:02.560 TVRec(1): Changing from Watching RecordingOnly to None
2010-02-24 11:00:02.644 Finished recording The Dr. Oz Show: channel 1013
2010-02-24 11:00:02.672 Unknown type, recording width was 0
2010-02-24 11:00:02.885 Finished recording The Dr. Oz Show: channel 1013
2010-02-24 11:00:03.014 mythbackend version: branches/release-0-22-fixes [22594] www.mythtv.org
2010-02-24 11:00:03.021 TVRec(1): Changing from None to Watching RecordingOnly
2010-02-24 11:00:03.059 Using runtime prefix = /usr
2010-02-24 11:00:03.091 TVRec(1): HW Tuner: 1->1
2010-02-24 11:00:03.130 Using configuration directory = /home/mythtv/.mythtv
2010-02-24 11:00:03.232 Empty LocalHostName.
2010-02-24 11:00:03.262 Using localhost value of htpc2
2010-02-24 11:00:03.294 MPEGRec(/dev/video0) Warning: Stream type 'DVD-Special 2'
			is not supported by ivtv driver, using 'DVD' instead.
2010-02-24 11:00:03.305 Testing network connectivity to '192.168.0.6'
2010-02-24 11:00:03.424 New DB connection, total: 1
2010-02-24 11:00:03.459 Connected to database 'mythconverg' at host: 192.168.0.6
2010-02-24 11:00:03.487 Closing DB connection named 'DBManager0'
2010-02-24 11:00:03.518 Connected to database 'mythconverg' at host: 192.168.0.6
2010-02-24 11:00:03.553 Current MythTV Schema Version (DBSchemaVer): 1244
2010-02-24 11:00:03.580 New DB connection, total: 2
2010-02-24 11:00:03.533 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2010-02-24 11:00:03.610 Connected to database 'mythconverg' at host: 192.168.0.6
2010-02-24 11:00:03.651 Started recording: The Young and the Restless "Katherine Makes an Unexpected Move": channel 1012 on cardid 1, sourceid 1
2010-02-24 11:00:04.801 Reschedule requested for id 0.
2010-02-24 11:00:05.185 Scheduled 128 items in 0.4 = 0.05 match + 0.33 place
2010-02-24 11:00:08.742 AFD: Opened codec 0x962d4e0, id(MPEG2VIDEO) type(Video)
2010-02-24 11:00:08.819 AFD: codec MP2 has 2 channels
2010-02-24 11:00:08.849 AFD: Opened codec 0x962da50, id(MP2) type(Audio)
2010-02-24 11:00:09.065 Preview: Grabbed preview '/myth/recordings/1013_20100224095800.mpg' 720x480@184s
2010-02-24 11:00:44.056 JobQueue: Commercial Flagging Starting for The Dr. Oz Show recorded from channel 1013 at Wed Feb 24 09:58:00 2010
2010-02-24 11:00:44.195 Using runtime prefix = /usr
2010-02-24 11:00:44.218 Using configuration directory = /home/mythtv/.mythtv
2010-02-24 11:00:44.249 Empty LocalHostName.
2010-02-24 11:00:44.280 Using localhost value of htpc2
2010-02-24 11:00:44.306 Testing network connectivity to '192.168.0.6'
2010-02-24 11:00:44.344 New DB connection, total: 1
2010-02-24 11:00:44.366 Connected to database 'mythconverg' at host: 192.168.0.6
2010-02-24 11:00:44.382 Closing DB connection named 'DBManager0'
2010-02-24 11:00:44.403 Connected to database 'mythconverg' at host: 192.168.0.6
2010-02-24 11:00:44.437 New DB connection, total: 2
2010-02-24 11:00:44.454 Connected to database 'mythconverg' at host: 192.168.0.6
2010-02-24 11:00:44.612 MythContext: Connecting to backend server: 192.168.0.6:6543 (try 1 of 1)
2010-02-24 11:00:44.627 Using protocol version 50
2010-02-24 11:00:44.647 MainServer::ANN Monitor
2010-02-24 11:00:44.678 adding: htpc2 as a client (events: 0)
2010-02-24 11:00:44.698 MainServer::ANN Monitor
2010-02-24 11:00:44.728 adding: htpc2 as a client (events: 1)
2010-02-24 11:00:45.829 RingBuf(/myth/recordings/1013_20100224095800.mpg): Waited 1.0 seconds for data to become available...
2010-02-24 11:00:46.889 RingBuf(/myth/recordings/1013_20100224095800.mpg): Waited 2.0 seconds for data to become available...
2010-02-24 11:00:47.234 AFD: Opened codec 0x82749e0, id(MPEG2VIDEO) type(Video)
2010-02-24 11:00:47.262 AFD: codec MP2 has 2 channels
2010-02-24 11:00:47.292 AFD: Opened codec 0x82265d0, id(MP2) type(Audio)
2010-02-24 11:00:47.500 [mp2 @ 0x6d016c0]Header missing
2010-02-24 11:00:47.628 AFD Error: Unknown audio decoding error
2010-02-24 11:00:47.827 [mp2 @ 0x6d016c0]Header missing
2010-02-24 11:00:47.873 AFD Error: Unknown audio decoding error
2010-02-24 11:00:48.030 [mpeg2video @ 0x6d016c0]Missing picture start code
(The above line repeats like a billion times)
2010-02-24 11:05:56.250 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2010-02-24 11:05:56.311 Expiring 2300 MBytes for 1013 @ Thu Feb 4 09:58:00 2010 => The Dr. Oz Show.  Too many episodes, we only want to keep 10.
2010-02-24 11:05:56.339 Expiring 0 MBytes for 1013 @ Wed Feb 3 09:58:01 2010 => The Dr. Oz Show.  Too many episodes, we only want to keep 10.
2010-02-24 11:05:56.353 Reschedule requested for id 0.
2010-02-24 11:05:56.761 Scheduled 128 items in 0.4 = 0.05 match + 0.36 place
2010-02-24 11:05:56.787 Reschedule requested for id 0.
2010-02-24 11:05:57.186 Scheduled 128 items in 0.4 = 0.03 match + 0.36 place
2010-02-24 11:05:59.365 Error deleting '/myth/recordings/1013_20100204095800.mpg' could not open 
			eno: Permission denied (13)
2010-02-24 11:05:59.433 Delete Error '/myth/recordings/1013_20100204095800.mpg'
			eno: Permission denied (13)
2010-02-24 11:05:59.464 Error deleting file: /myth/recordings/1013_20100204095800.mpg. Keeping metadata in database.
2010-02-24 11:05:59.505 Error deleting '/myth/recordings/1013_20100203095801.mpg' could not open 
			eno: Permission denied (13)
2010-02-24 11:05:59.586 Delete Error '/myth/recordings/1013_20100203095801.mpg'
			eno: Permission denied (13)
2010-02-24 11:05:59.617 Error deleting file: /myth/recordings/1013_20100203095801.mpg. Keeping metadata in database.
2010-02-24 11:16:51.472 MainServer::ANN Monitor
2010-02-24 11:16:51.532 adding: old-frontend as a client (events: 0)
2010-02-24 11:17:02.654 MainServer::ANN Monitor
2010-02-24 11:17:02.701 adding: htpc2 as a client (events: 0)
2010-02-24 11:20:04.774 UPnpMedia: BuildMediaMap VIDEO scan starting in :/myth/videos:
2010-02-24 11:20:04.891 UPnpMedia: BuildMediaMap Done. Found 155 objects
2010-02-24 11:20:56.563 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2010-02-24 11:20:56.617 Expiring 2300 MBytes for 1013 @ Thu Feb 4 09:58:00 2010 => The Dr. Oz Show.  Too many episodes, we only want to keep 10.
2010-02-24 11:20:56.642 Expiring 0 MBytes for 1013 @ Wed Feb 3 09:58:01 2010 => The Dr. Oz Show.  Too many episodes, we only want to keep 10.
2010-02-24 11:20:56.654 Reschedule requested for id 0.
2010-02-24 11:20:57.114 Scheduled 128 items in 0.5 = 0.05 match + 0.41 place
2010-02-24 11:20:57.152 Reschedule requested for id 0.
2010-02-24 11:20:57.519 Scheduled 128 items in 0.4 = 0.03 match + 0.33 place
2010-02-24 11:20:59.665 Error deleting '/myth/recordings/1013_20100204095800.mpg' could not open 
			eno: Permission denied (13)
2010-02-24 11:20:59.696 Delete Error '/myth/recordings/1013_20100204095800.mpg'
			eno: Permission denied (13)
2010-02-24 11:20:59.726 Error deleting file: /myth/recordings/1013_20100204095800.mpg. Keeping metadata in database.
2010-02-24 11:20:59.763 Error deleting '/myth/recordings/1013_20100203095801.mpg' could not open 
			eno: Permission denied (13)
2010-02-24 11:20:59.863 Delete Error '/myth/recordings/1013_20100203095801.mpg'
			eno: Permission denied (13)
2010-02-24 11:20:59.890 Error deleting file: /myth/recordings/1013_20100203095801.mpg. Keeping metadata in database.
2010-02-24 11:27:05.664 [mpeg2video @ 0x6d016c0]Warning MVs not available
2010-02-24 11:28:00.240 [mpeg2video @ 0x6d016c0]ac-tex damaged at 30 9
2010-02-24 11:28:00.284 [mpeg2video @ 0x6d016c0]Warning MVs not available
2010-02-24 11:28:02.965 mythbackend version: branches/release-0-22-fixes [22594] www.mythtv.org
2010-02-24 11:28:03.021 Using runtime prefix = /usr
2010-02-24 11:28:03.052 Using configuration directory = /home/mythtv/.mythtv
2010-02-24 11:28:03.083 Empty LocalHostName.
2010-02-24 11:28:03.113 Using localhost value of htpc2
2010-02-24 11:28:03.144 Testing network connectivity to '192.168.0.6'
2010-02-24 11:28:03.271 New DB connection, total: 1
2010-02-24 11:28:03.312 Connected to database 'mythconverg' at host: 192.168.0.6
2010-02-24 11:28:03.337 Closing DB connection named 'DBManager0'
2010-02-24 11:28:03.369 Connected to database 'mythconverg' at host: 192.168.0.6
2010-02-24 11:28:03.403 Current MythTV Schema Version (DBSchemaVer): 1244
2010-02-24 11:28:03.431 New DB connection, total: 2
2010-02-24 11:28:03.460 Connected to database 'mythconverg' at host: 192.168.0.6
2010-02-24 11:28:08.354 AFD: Opened codec 0x84a24e0, id(MPEG2VIDEO) type(Video)
2010-02-24 11:28:08.383 AFD: codec MP2 has 2 channels
2010-02-24 11:28:08.413 AFD: Opened codec 0x84a2a50, id(MP2) type(Audio)
2010-02-24 11:28:08.575 Preview: Grabbed preview '/myth/recordings/1013_20100224095800.mpg' 720x480@184s
2010-02-24 11:35:56.775 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2010-02-24 11:35:56.846 Expiring 2300 MBytes for 1013 @ Thu Feb 4 09:58:00 2010 => The Dr. Oz Show.  Too many episodes, we only want to keep 10.
2010-02-24 11:35:56.877 Expiring 0 MBytes for 1013 @ Wed Feb 3 09:58:01 2010 => The Dr. Oz Show.  Too many episodes, we only want to keep 10.
2010-02-24 11:35:56.890 Reschedule requested for id 0.
2010-02-24 11:35:57.284 Scheduled 128 items in 0.4 = 0.05 match + 0.34 place
2010-02-24 11:35:57.316 Reschedule requested for id 0.
2010-02-24 11:35:57.680 Scheduled 128 items in 0.4 = 0.03 match + 0.33 place
2010-02-24 11:35:59.898 Error deleting '/myth/recordings/1013_20100204095800.mpg' could not open 
			eno: Permission denied (13)
2010-02-24 11:35:59.965 Delete Error '/myth/recordings/1013_20100204095800.mpg'
			eno: Permission denied (13)
2010-02-24 11:35:59.992 Error deleting file: /myth/recordings/1013_20100204095800.mpg. Keeping metadata in database.
2010-02-24 11:36:00.032 Error deleting '/myth/recordings/1013_20100203095801.mpg' could not open 
			eno: Permission denied (13)
2010-02-24 11:36:00.064 Delete Error '/myth/recordings/1013_20100203095801.mpg'
			eno: Permission denied (13)
2010-02-24 11:36:00.095 Error deleting file: /myth/recordings/1013_20100203095801.mpg. Keeping metadata in database.
2010-02-24 11:50:07.937 UPnpMedia: BuildMediaMap VIDEO scan starting in :/myth/videos:
2010-02-24 11:50:08.084 UPnpMedia: BuildMediaMap Done. Found 155 objects
2010-02-24 11:50:57.007 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2010-02-24 11:50:57.067 Expiring 2300 MBytes for 1013 @ Thu Feb 4 09:58:00 2010 => The Dr. Oz Show.  Too many episodes, we only want to keep 10.
2010-02-24 11:50:57.096 Expiring 0 MBytes for 1013 @ Wed Feb 3 09:58:01 2010 => The Dr. Oz Show.  Too many episodes, we only want to keep 10.
2010-02-24 11:50:57.108 Reschedule requested for id 0.
2010-02-24 11:50:57.496 Scheduled 128 items in 0.4 = 0.05 match + 0.33 place
2010-02-24 11:50:57.525 Reschedule requested for id 0.
2010-02-24 11:50:57.888 Scheduled 128 items in 0.4 = 0.03 match + 0.33 place
2010-02-24 11:51:00.115 Error deleting '/myth/recordings/1013_20100204095800.mpg' could not open 
			eno: Permission denied (13)
2010-02-24 11:51:00.161 Delete Error '/myth/recordings/1013_20100204095800.mpg'
			eno: Permission denied (13)
2010-02-24 11:51:00.191 Error deleting file: /myth/recordings/1013_20100204095800.mpg. Keeping metadata in database.
2010-02-24 11:51:00.231 Error deleting '/myth/recordings/1013_20100203095801.mpg' could not open 
			eno: Permission denied (13)
2010-02-24 11:51:00.273 Delete Error '/myth/recordings/1013_20100203095801.mpg'
			eno: Permission denied (13)

```

I can attach the full mythbackend.log if that helps.

BTW, I'm running a Hauppauge PVR-150.  Is anybody else having this problem?  Hopefully this bug is fixed in 10.04.

-teet

---

### Post by nickrout on 2010-02-25
I suspect your database is corrupt. run the optimize program.

---

### Post by teet on 2010-02-25
I'm not sure what the optimize program is?  But, I ran a "mysqlcheck -r" last night and it did not report any errors.

Thanks for your reply!

-teet

---

### Post by nickrout on 2010-02-25
the wiki has most answers:

[http://www.mythtv.org/wiki/Optimize_mythdb.pl](http://www.mythtv.org/wiki/Optimize_mythdb.pl)

---

### Post by teet on 2010-02-26
I ran the optimize script.  The log output did not indicate any errors.  It just said that it repaired/optimized a bunch of things.

We'll see what happens tomorrow.  I don't think this is going to fix the problem but you never know.

-teet

Edit 1:  What happened to the "optimize database daily" option that used to be in the mythbuntu control center?

Edit 2:  I just noticed that it recorded shows again today under the "alex" user instead of the "mythtv" user.  See screenshot.

---

### Post by teet on 2010-02-26
I checked again today and the problem persists.  I am still getting duplicate blank recordings.  I have ran mysqlcheck -r and the optimize script so I don't think the problem is with the mysql database.  I think the problem is that myth is recording stuff under the wrong user/group/permissions...and I have no idea how to change that.

Another thing I forgot to mention:  In mythweb, it will sometimes say a show is still recording days after it has ended.  A reboot usually fixes this.

-teet

---

### Post by nickrout on 2010-02-26
which user is running mythbackend?

```
pa aux|grep mythback
```

---

### Post by teet on 2010-02-26
I assume you meant "ps aux|grep mythback"

```

mythtv    2308  0.0  0.0   2936  1480 ?        Ss   Feb25   0:00 /bin/su -c /usr/bin/mythbackend --logfile /var/log/mythtv/mythbackend.log mythtv
mythtv    2327  0.0  0.0   1752   480 ?        S    Feb25   0:00 sh -c /usr/bin/mythbackend --logfile /var/log/mythtv/mythbackend.log
mythtv    2331  0.0  1.8 286824 38756 ?        Sl   Feb25   0:25 /usr/bin/mythbackend --logfile /var/log/mythtv/mythbackend.log
alex      3837  0.2  2.3 194840 48352 ?        Sl   Feb25   2:04 mythbackend
alex     27555  0.0  0.0   3044   804 pts/0    R+   16:17   0:00 grep mythback

```

It seems mythbackend is being run under the "alex" user.  I think we're getting closer.

-teet

Edit:  When I installed ubuntu, I simply created an entry in "Startup Applications" to start mythbackend.  I think this is where the problem is.  What is the proper way to start mythbackend automatically?  Or can I do something along the lines of 'mythbackend -u mythtv'.  FWIW I've been starting mythbackend since 7.04 this way and have never had any problems with it.

Edit2:  I just unticked the entry in startup applications and rebooted.  The backend seems to have started on its own.  The 'ps aux|grep mythback' still shows that "alex" is running mythbackend.

---

### Post by nickrout on 2010-02-26
yes sorry for the typo, or maybe i was just testing you LOL

mythbackend is started by /etc/init.d/mythtv-backend which is set to start in the default runlevel. It should be running as user mythtv, whereas mythfrontend should be running as the user you setup on install (probably alex in your setup).

---

### Post by teet on 2010-02-27
> **nickrout said:**
> yes sorry for the typo, or maybe i was just testing you LOL

mythbackend is started by /etc/init.d/mythtv-backend which is set to start in the default runlevel. It should be running as user mythtv, whereas mythfrontend should be running as the user you setup on install (probably alex in your setup).

You know the funny thing is that I read your post and then I "accidentally" typed "ps aux" instead of "pa aux".  I'm not really familiar with the ps aux command but I guess I've been hacking around on linux long enough to recognize it.  In this case I guess 2 wrongs do make a right.

Myth has recorded 3 shows now without any of that duplicate blank recording nonsense.  I'll give it a few more days but I think this fixed it.  I guess there were 2 mythbackends running (one from the /etc/init.d and the other from my startup applications).  All this time I have been thinking myth 0.22 was a buggy piece of junk!

Thanks for your help.

-teet

---

### Post by teet on 2010-03-07
Just as a followup, myth is working great now.  No problems in the past week.  The duplicate blank recordings and weird permissions problems were due to mythbackend being started both by the /etc/init.d/mythtv-backend and by running "mythbackend" as a "Startup Application".

Thanks again for pointing me in the right direction nickrout!

-teet

---

### Post by nickrout on 2010-03-07
my pleasure :)

---

