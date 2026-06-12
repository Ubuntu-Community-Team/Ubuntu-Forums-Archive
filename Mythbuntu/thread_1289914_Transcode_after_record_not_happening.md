---
title: "Transcode after record not happening"
date: 2009-10-12
forum: Mythbuntu
---

### Post by sawbuck on 2009-10-12
Point me to the right forum if this isn't it------

I'm running Mythbuntu 9.04 (up to date and updated frequently. I have set up "Job Queue (Global)"  with the "Run Transcode Jobs before auto-commercialflag" option checked - which according to the description flashed at the bottom of the screen should transcode the file first before flagging commercials.

I have tried a number of transcode profiles set to trigger immediately after recording but it never happens,  It jumps directly into commercial flagging and never transcodes.  As a result,  most commercials ARE flagged in the right location but - due to no transcoding - audio and video is choppy when viewed and/or twitchy when in the edit mode to refine commercial locations.  I can transcode manually with no difficulty but I'd really like to have it done automagically.  I've included my Frontend/backend system config below followed by a chunk of the mythbackend log.  Nowhere between the recording end point (first red timeline) to where it starts flagging commercials do IO see any hint of transcoding or an error because it couldn't.  Did I miss something?

As I said, I can manually transcode which I usually do after confirming/refining commercioal flagging - from HD broadcast density of 1920x1088) - down to STD 720x480 where it playsback fine.  However, I'd still like to have it done automatically.  And spend the time naiing down other nagging issues......

Can anyone help?

-------------------------------

Here's my system:

Motherboard: ASUS P4B533
CPU: Intel 2.4 Ghz
RAM: 2 Gb
Video Card: EVGA 6200 AGP 8x 512 Mb (NVIDIA GeForce chip)
Sound Card: integrated onboard C-Media Electronics Inc CM8738 (rev 10)
HD: maxtor 250Gb
Remote: none
Tuners: Haupauge HVR 1600 (using only ATSC)
Country: US
TV provider: US Broadcast
TV signal type: Digital (HD & DTV)
Mythbuntu Version: 9.04

--------------------------------

Here's a piece of the most recent attempt (from mythbackend log):

[COLOR=Red]2009-10-11 22:03:01.728 Finished recording Three Rivers "Ryan's First Day": channel 1041
[/COLOR]2009-10-11 22:03:04.182 Using runtime prefix = /usr
2009-10-11 22:03:04.245 Empty LocalHostName.
2009-10-11 22:03:04.246 Using localhost value of Frank4
2009-10-11 22:03:04.425 New DB connection, total: 1
2009-10-11 22:03:04.517 Connected to database 'mythconverg' at host: Frank4
2009-10-11 22:03:04.519 Closing DB connection named 'DBManager0'
2009-10-11 22:03:04.521 Connected to database 'mythconverg' at host: Frank4
2009-10-11 22:03:04.553 New DB connection, total: 2
2009-10-11 22:03:04.555 Connected to database 'mythconverg' at host: Frank4
2009-10-11 22:03:04.559 Current Schema Version: 1214
2009-10-11 22:03:07.523 AFD: Opened codec 0x9b22400, id(MPEG2VIDEO) type(Video)
2009-10-11 22:03:07.524 AFD: codec AC3 has 6 channels
2009-10-11 22:03:07.530 AFD: Opened codec 0x9b229f0, id(AC3) type(Audio)
2009-10-11 22:03:07.534 AFD: codec AC3 has 2 channels
2009-10-11 22:03:07.538 AFD: Opened codec 0x9b22fe0, id(AC3) type(Audio)
[COLOR=Red]2009-10-11 22:03:07.543 AFD: Opened codec 0x9b235d0, id(MPEG1VIDEO) type(Video)
2009-10-11 22:03:08.202 Preview: Grabbed preview '/var/lib/mythtv/recordings/1041_20091011205700.mpg' 1920x1088@64s
2009-10-11 22:03:35.636 JobQueue: Commercial Flagging Starting for Three Rivers "Ryan's First Day" [/COLOR]recorded from channel 1041 at Sun Oct 11 20:57:00 2009
2009-10-11 22:03:35.852 Using runtime prefix = /usr
2009-10-11 22:03:35.857 Empty LocalHostName.
2009-10-11 22:03:35.858 Using localhost value of Frank4
2009-10-11 22:03:35.870 New DB connection, total: 1
2009-10-11 22:03:35.878 Connected to database 'mythconverg' at host: Frank4
2009-10-11 22:03:35.880 Closing DB connection named 'DBManager0'
2009-10-11 22:03:35.887 Connected to database 'mythconverg' at host: Frank4
2009-10-11 22:03:35.900 New DB connection, total: 2
2009-10-11 22:03:35.903 Connected to database 'mythconverg' at host: Frank4
2009-10-11 22:03:35.928 Connecting to backend server: 192.168.1.104:6543 (try 1 of 5)
2009-10-11 22:03:35.931 Using protocol version 40
2009-10-11 22:03:35.932 MainServer::HandleAnnounce Monitor
2009-10-11 22:03:35.938 adding: Frank4 as a client (events: 0)
2009-10-11 22:03:35.947 MainServer::HandleAnnounce Monitor
2009-10-11 22:03:35.954 adding: Frank4 as a client (events: 1)
2009-10-11 22:03:37.222 RingBuf(/var/lib/mythtv/recordings/1041_20091011205700.mpg): Waited 1.0 seconds for data to become available...
2009-10-11 22:03:38.226 RingBuf(/var/lib/mythtv/recordings/1041_20091011205700.mpg): Waited 2.0 seconds for data to become available...
2009-10-11 22:03:38.567 AFD: Opened codec 0x9502e60, id(MPEG2VIDEO) type(Video)
2009-10-11 22:03:38.569 AFD: codec AC3 has 6 channels
2009-10-11 22:03:38.570 AFD: Opened codec 0x9503450, id(AC3) type(Audio)
2009-10-11 22:03:38.571 AFD: codec AC3 has 2 channels
2009-10-11 22:03:38.579 AFD: Opened codec 0x9503a40, id(AC3) type(Audio)
2009-10-11 22:03:38.588 AFD: Opened codec 0x9504030, id(MPEG1VIDEO) type(Video)
2009-10-11 22:05:50.877 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-11 22:10:25.469 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2009-10-11 22:10:25.475 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-10-11 22:20:50.931 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-11 22:35:50.983 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-11 22:40:30.478 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2009-10-11 22:40:30.482 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-10-11 22:50:51.061 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-11 23:05:51.180 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-11 23:10:37.485 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2009-10-11 23:10:37.490 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-10-11 23:17:07.536 [mpeg2video @ 0xb74bb744]ac-tex damaged at 85 7
2009-10-11 23:17:07.592 [mpeg2video @ 0xb74bb744]Warning MVs not available
2009-10-11 23:17:10.973 Using runtime prefix = /usr
2009-10-11 23:17:11.026 Empty LocalHostName.
2009-10-11 23:17:11.030 Using localhost value of Frank4
2009-10-11 23:17:11.181 New DB connection, total: 1
2009-10-11 23:17:11.278 Connected to database 'mythconverg' at host: Frank4
2009-10-11 23:17:11.284 Closing DB connection named 'DBManager0'
2009-10-11 23:17:11.286 Connected to database 'mythconverg' at host: Frank4
2009-10-11 23:17:11.288 New DB connection, total: 2
2009-10-11 23:17:11.291 Connected to database 'mythconverg' at host: Frank4
2009-10-11 23:17:11.296 Current Schema Version: 1214
2009-10-11 23:17:11.953 AFD: Opened codec 0x988d3f0, id(MPEG2VIDEO) type(Video)
2009-10-11 23:17:11.955 AFD: codec AC3 has 6 channels
2009-10-11 23:17:11.959 AFD: Opened codec 0x988d9e0, id(AC3) type(Audio)
2009-10-11 23:17:11.962 AFD: codec AC3 has 2 channels
2009-10-11 23:17:11.967 AFD: Opened codec 0x988dfd0, id(AC3) type(Audio)
2009-10-11 23:17:11.971 AFD: Opened codec 0x988e5c0, id(MPEG1VIDEO) type(Video)
2009-10-11 23:17:12.510 Preview: Grabbed preview '/var/lib/mythtv/recordings1041_20091011205700.mpg' 1920x1088@64s
2009-10-11 23:20:51.250 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-11 23:35:51.296 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-11 23:40:37.493 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2009-10-11 23:40:37.499 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-10-11 23:50:51.336 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-12 00:05:51.378 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-12 00:10:41.501 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2009-10-12 00:10:41.507 UPnpMedia: BuildMediaMap Done. Found 0 objects

---

### Post by sawbuck on 2009-10-14
Still ain't happening.  Everything I've read seems to say it should....

---

### Post by sawbuck on 2009-10-19
This is a real oops.....

My software engineer son, who has been running myth a probably a decade, solved my problem.  As it turns out I had inadvertently unchecked the "auto-transcode after recording" in my recording "Default" encoder recording profile probably while rechecking my setup early on.  Obviously, without activation auto-transcode it ain't never gointg to....duh.

I've caught a few errors like that myself since it is easy to hit the wrong arrow key when progressing through setup pages.  Or even miss it when rechecking but I'm really red-faced   over missing the blatantly obvious.

A lesson here... take nothing for granted in verifying a setup and verify carefully..

---

