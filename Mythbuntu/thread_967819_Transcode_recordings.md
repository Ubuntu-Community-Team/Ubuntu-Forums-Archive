---
title: "Transcode recordings"
date: 2008-11-02
forum: Mythbuntu
---

### Post by MailerDaemon on 2008-11-02
Hi, thanks to newlinux my system now works :D But I have a problem with the transcoding of recordings.
I successfull flag the commercials but when i try to transcode the recordings there is an error:

Umwandeln (Fehler: 2.11.2008, 16:14)
exit status 255, job status was "Errored"

here is the log of the master backend:


```

2008-11-02 16:14:33.785 New DB connection, total: 2
2008-11-02 16:14:33.787 Connected to database 'mythconverg' at host: localhost
2008-11-02 16:14:33.799 Transcoding from /var/lib/mythtv/recordings/13003_20081102144500.mpg to /var/lib/mythtv/recordings/13003_20081102144500.mpg.tmp
2008-11-02 16:14:33.818 Connecting to backend server: 192.168.0.101:6543 (try 1 of 5)
2008-11-02 16:14:33.821 Using protocol version 40
2008-11-02 16:14:33.827 MainServer::HandleAnnounce Monitor
2008-11-02 16:14:33.834 adding: till-media as a client (events: 0)
2008-11-02 16:14:33.844 MainServer::HandleAnnounce Monitor
2008-11-02 16:14:33.850 adding: till-media as a client (events: 1)
2008-11-02 16:14:36.335 AFD: Opened codec 0xa19f420, id(MPEG2VIDEO) type(Video)
2008-11-02 16:14:36.339 AFD: codec MP3 has 2 channels
2008-11-02 16:14:36.340 AFD: Opened codec 0xa19fa10, id(MP3) type(Audio)
2008-11-02 16:14:36.347 AFD: codec AC3 has 2 channels
2008-11-02 16:14:36.356 AFD: Opened codec 0xa1a05f0, id(AC3) type(Audio)
2008-11-02 16:14:36.419 Transcode: Looking for autodetect profile: Autodetect from 576i
2008-11-02 16:14:36.423 New DB connection, total: 3
2008-11-02 16:14:36.425 Connected to database 'mythconverg' at host: localhost
2008-11-02 16:14:36.447 Transcode: Using autodetect profile: MPEG2
2008-11-02 16:14:36.448 No video information found!
2008-11-02 16:14:36.449 Please ensure that recording profiles for the transcoder are set
2008-11-02 16:14:36.455 Transcoding /var/lib/mythtv/recordings/13003_20081102144500.mpg failed
2008-11-02 16:14:36.468 Deleting /var/lib/mythtv/recordings/13003_20081102144500.mpg.tmp
2008-11-02 16:14:36.472 Error Truncating '/var/lib/mythtv/recordings/13003_20081102144500.mpg.tmp' could not stat 
			eno: No such file or directory (2), unlinking immediately.
2008-11-02 16:14:36.501 JobQueue: Transcode Errored: Bauer sucht Frau "TV-Romanze mit Inka Bause": Autodetect (exit status 255, job status was "Errored")
2008-11-02 16:14:38.892 MainServer::HandleAnnounce Monitor
2008-11-02 16:14:38.896 adding: till-media as a client (events: 0)
2008-11-02 16:15:13.540 MainServer::HandleAnnounce Monitor
2008-11-02 16:15:13.541 adding: till-media as a client (events: 0)
2008-11-02 16:15:13.543 MainServer::HandleAnnounce Monitor
2008-11-02 16:15:13.545 adding: till-media as a client (events: 1)
2008-11-02 16:16:00.382 Reschedule requested for id -1.
2008-11-02 16:16:00.411 Scheduled 0 items in 0.0 = 0.01 match + 0.02 place
2008-11-02 16:17:33.521 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-11-02 16:17:33.529 UPnpMedia: BuildMediaMap Done. Found 0 objects
2008-11-02 16:18:33.681 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-02 16:18:50.383 DVBSM(0), Warning: Can not count Uncorrected Blocks
			eno: Function not implemented (38)
2008-11-02 16:19:53.631 Reschedule requested for id -1.
2008-11-02 16:19:53.682 Scheduled 0 items in 0.1 = 0.01 match + 0.04 place

```

i hope someone can help me

thanks,

Till

---

### Post by dmfrey on 2008-11-02
Go into your recording profiles and set them to be mpeg4.  That worked for me.

---

