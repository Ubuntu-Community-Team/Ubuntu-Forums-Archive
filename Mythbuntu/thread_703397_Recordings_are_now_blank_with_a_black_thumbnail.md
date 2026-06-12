---
title: "Recordings are now blank with a black thumbnail"
date: 2008-02-21
forum: Mythbuntu
---

### Post by sephiro499 on 2008-02-21
I have a celeron 766 with a pvr 150 and a cheap pinnacle frame grabber.  Everything was working great until I tried to record to programs at the same time so as to use both tuners.  Wanted to test since I wasn't sure my machine had the muscle to handle it.  The two recordings that followed were both black thumbnails with no video or audio.  Now all recordings basically record nothing:

2008-02-20 09:43:09.003 adding: sephiro499-desktop as a client (events: 0)
2008-02-20 19:36:26.656 MainServer::HandleAnnounce Monitor
2008-02-20 19:36:26.663 adding: sephiro499-desktop as a client (events: 0)
2008-02-20 19:36:29.288 MainServer::HandleAnnounce Monitor
2008-02-20 19:36:29.292 adding: sephiro499-desktop as a client (events: 0)
2008-02-20 20:34:32.120 MainServer::HandleAnnounce Monitor
2008-02-20 20:34:32.123 adding: sephiro499-desktop as a client (events: 0)
2008-02-20 20:36:10.398 MainServer::HandleAnnounce Monitor
2008-02-20 20:36:10.404 adding: sephiro499-desktop as a client (events: 0)
2008-02-20 20:38:05.123 MainServer::HandleAnnounce Monitor
2008-02-20 20:38:05.128 adding: sephiro499-desktop as a client (events: 0)
2008-02-20 20:38:15.909 MainServer::HandleAnnounce Monitor
2008-02-20 20:38:15.911 adding: sephiro499-desktop as a client (events: 0)
2008-02-20 22:30:02.301 TVRec(1): Changing from None to RecordingOnly
2008-02-20 22:30:02.313 TVRec(1): HW Tuner: 1->1
2008-02-20 22:30:02.585 Unknown video codec
2008-02-20 22:30:02.595 Please go into the TV Settings, Recording Profiles and
2008-02-20 22:30:02.596 setup the four 'Software Encoders' profiles.
2008-02-20 22:30:02.597 Assuming RTjpeg for now.
2008-02-20 22:30:02.599 NVR: Error, unknown audio codec
2008-02-20 22:30:02.707 Started recording: Naruto "Father and Son, the Broken Crest": channel 1040 on cardid 1, sourceid 1
VIDIOCSYNC: Input/output error
VIDIOCSYNC: Input/output error
VIDIOCSYNC: Input/output error
VIDIOCSYNC: Input/output error
VIDIOCSYNC: Input/output error
VIDIOCSYNC: Input/output error
VIDIOCSYNC: Input/output error
VIDIOCSYNC: Input/output error
VIDIOCSYNC: Input/output error
2008-02-20 22:30:05.231 NVR: Multiple bttv errors, further messages supressed
2008-02-20 23:00:00.847 TVRec(1): Changing from RecordingOnly to None
2008-02-20 23:00:00.871 Finished recording Naruto "Father and Son, the Broken Crest": channel 1040
2008-02-20 23:00:00.936 Reschedule requested for id 0.
2008-02-20 23:00:01.052 Scheduled 5 items in 0.1 = 0.01 match + 0.11 place
2008-02-20 23:00:01.931 Finished recording Naruto "Father and Son, the Broken Crest": channel 1040
2008-02-20 23:00:01.997 0 length seek table
2008-02-20 23:00:02.011 NVP: Recording does not have position map.
                        Run 'mythcommflag --file 1040_20080220223000.nuv --rebuild' to fix
2008-02-20 23:00:47.498 JobQueue: Commercial Flagging Starting for Naruto "Father and Son, the Broken Crest" recorded from channel 1040 at Wed Feb 20 22:30:00
 2008
2008-02-20 23:00:47.867 Using runtime prefix = /usr
2008-02-20 23:00:47.959 New DB connection, total: 1
2008-02-20 23:00:47.977 Connected to database 'mythconverg' at host: localhost
2008-02-20 23:00:48.001 New DB connection, total: 2
2008-02-20 23:00:48.006 Connected to database 'mythconverg' at host: localhost
2008-02-20 23:00:48.061 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-02-20 23:00:48.068 Using protocol version 31
2008-02-20 23:00:48.071 MainServer::HandleAnnounce Monitor
2008-02-20 23:00:48.075 adding: sephiro499-desktop as a client (events: 0)
2008-02-20 23:00:48.079 MainServer::HandleAnnounce Monitor
2008-02-20 23:00:48.081 adding: sephiro499-desktop as a client (events: 1)
2008-02-20 23:00:48.242 0 length seek table
2008-02-20 23:00:57.777 RingBuf(/var/lib/mythtv/recordings/1040_20080220223000.nuv): Waited 1.0 seconds for data to become available...
2008-02-20 23:00:58.789 RingBuf(/var/lib/mythtv/recordings/1040_20080220223000.nuv): Waited 2.0 seconds for data to become available...
2008-02-20 23:01:00.028 JobQueue: Commercial Flagging Finished, 0 break(s) found.
2008-02-20 23:01:00.084 0 length seek table
2008-02-20 23:01:00.094 NVP: Recording does not have position map.
                        Run 'mythcommflag --file 1040_20080220223000.nuv --rebuild' to fix
sephiro499@sephiro499-desktop:~$


Also after I rebooted the machine mythtv setup magically forgot it's IP address and mythweb and the frontend fails until I run mythtv setup again and input the correct ip address; all other settings stayed the same but the IP address.

---

### Post by foxbuntu on 2008-02-22
This sounds like two seperate issues. 

1) The Black video issue: Does it go away after reboot? How much ram is in the machine?

2) What are you using for DHCP and how long of a DHCP lease is it providing?

---

### Post by sephiro499 on 2008-02-22
768 ram  I had an issue with DHCP setting the hostname and i disabled dhcp and use a static IP.  I think the settings problem though might have been from an improper shutdown.

Here is a copy of the log when I was having the problems with the framegrabber.


2008-02-20 22:30:02.301 TVRec(1): Changing from None to RecordingOnly
2008-02-20 22:30:02.313 TVRec(1): HW Tuner: 1->1
2008-02-20 22:30:02.585 Unknown video codec
2008-02-20 22:30:02.595 Please go into the TV Settings, Recording Profiles and
2008-02-20 22:30:02.596 setup the four 'Software Encoders' profiles.
2008-02-20 22:30:02.597 Assuming RTjpeg for now.
2008-02-20 22:30:02.599 NVR: Error, unknown audio codec
2008-02-20 22:30:02.707 Started recording: Naruto "Father and Son, the Broken Cr
est": channel 1040 on cardid 1, sourceid 1
VIDIOCSYNC: Input/output error
VIDIOCSYNC: Input/output error
VIDIOCSYNC: Input/output error
VIDIOCSYNC: Input/output error
VIDIOCSYNC: Input/output error
VIDIOCSYNC: Input/output error
VIDIOCSYNC: Input/output error
VIDIOCSYNC: Input/output error
VIDIOCSYNC: Input/output error
2008-02-20 22:30:05.231 NVR: Multiple bttv errors, further messages supressed
2008-02-20 23:00:00.847 TVRec(1): Changing from RecordingOnly to None
2008-02-20 23:00:00.871 Finished recording Naruto "Father and Son, the Broken Crest": channel 1040
2008-02-20 23:00:00.936 Reschedule requested for id 0.
2008-02-20 23:00:01.052 Scheduled 5 items in 0.1 = 0.01 match + 0.11 place
2008-02-20 23:00:01.931 Finished recording Naruto "Father and Son, the Broken Crest": channel 1040
2008-02-20 23:00:01.997 0 length seek table
2008-02-20 23:00:02.011 NVP: Recording does not have position map.
                        Run 'mythcommflag --file 1040_20080220223000.nuv --rebuild' to fix
2008-02-20 23:00:47.498 JobQueue: Commercial Flagging Starting for Naruto "Father and Son, the Broken Crest" recorded from channel 1040 at Wed Feb 20 22:30:00
 2008
2008-02-20 23:00:47.867 Using runtime prefix = /usr
2008-02-20 23:00:47.959 New DB connection, total: 1
2008-02-20 23:00:47.977 Connected to database 'mythconverg' at host: localhost
2008-02-20 23:00:48.001 New DB connection, total: 2
2008-02-20 23:00:48.006 Connected to database 'mythconverg' at host: localhost
2008-02-20 23:00:48.061 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-02-20 23:00:48.068 Using protocol version 31
2008-02-20 23:00:48.071 MainServer::HandleAnnounce Monitor
2008-02-20 23:00:48.075 adding: sephiro499-desktop as a client (events: 0)
2008-02-20 23:00:48.079 MainServer::HandleAnnounce Monitor
2008-02-20 23:00:48.081 adding: sephiro499-desktop as a client (events: 1)
2008-02-20 23:00:48.242 0 length seek table
2008-02-20 23:00:57.777 RingBuf(/var/lib/mythtv/recordings/1040_20080220223000.nuv): Waited 1.0 seconds for data to become available...
2008-02-20 23:00:58.789 RingBuf(/var/lib/mythtv/recordings/1040_20080220223000.nuv): Waited 2.0 seconds for data to become available...
2008-02-20 23:01:00.028 JobQueue: Commercial Flagging Finished, 0 break(s) found.
2008-02-20 23:01:00.084 0 length seek table
2008-02-20 23:01:00.094 NVP: Recording does not have position map.
                        Run 'mythcommflag --file 1040_20080220223000.nuv --rebuild' to fix

---

