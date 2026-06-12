---
title: "Trouble recieving 11.1 CBS in Dallas"
date: 2009-05-12
forum: Mythbuntu
---

### Post by epi 1:10,000 on 2009-05-12
I'm using Time Warner Cable 256 QAM in Dallas for my local channels because using an exterior antenna is forbidden in my neighborhood and all the indoor solutions I have tried are in effective.  I'm able to get all the local channels except CBS 11.1/375.  It locks in the channel w/ a good signal, 2.6 S/N, and 0 BER but the screen freezes on the last frame from the previous channel.  My HVR-1250's and my HVR-1600 have a perfect picture on all my other channels w/ those signal, S/N, and BER rates. Has anyone else encountered this problem?  Are there any logs I can look in to try and figure out why this is happening?

---

### Post by klc5555 on 2009-05-12
> **epi 1:10,000 said:**
> I'm using Time Warner Cable 256 QAM in Dallas for my local channels because using an exterior antenna is forbidden in my neighborhood and all the indoor solutions I have tried are in effective.  I'm able to get all the local channels except CBS 11.1/375.  It locks in the channel w/ a good signal, 2.6 S/N, and 0 BER but the screen freezes on the last frame from the previous channel.  My HVR-1250's and my HVR-1600 have a perfect picture on all my other channels w/ those signal, S/N, and BER rates. Has anyone else encountered this problem?  Are there any logs I can look in to try and figure out why this is happening?

This sounds like livetv. Can you successfully schedule a recording on this channel, then later play it back (or at least see a correct animated thumbnail in "view recordings") in Mythtv or with an external player, like xine or mplayer or whatever? If so, then the backend is handling the channel OK, and recording, but the frontend is getting it wrong. If not, then the backend is likely not handling the channel correctly. The output from the mythbackend log or the mythfrontend log (as appropriate) in /var/log/mythtv/ from the time that the station is selected to be tuned can yield some clues.

---

### Post by epi 1:10,000 on 2009-05-13
I ham having the problem on live TV and  recordings.  Attached are my error logs.   Similar to  [http://svn.mythtv.org/trac/ticket/6369](http://svn.mythtv.org/trac/ticket/6369).



==> /var/log/mythtv/mythbackend.log <==
2009-05-13 05:35:01.209 TVRec(8): Changing from None to WatchingLiveTV
2009-05-13 05:35:01.215 TVRec(8): HW Tuner: 8->8
2009-05-13 05:35:02.569 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-05-13 05:35:02.856 Finished recording CBS 11 News This Morning at 5AM: channel 1111
2009-05-13 05:35:03.898 Finished recording CBS 11 News This Morning at 5AM: channel 1111
2009-05-13 05:35:03.914 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-05-13 05:35:04.090 Using runtime prefix = /usr
2009-05-13 05:35:04.095 Empty LocalHostName.
2009-05-13 05:35:04.097 Using localhost value of jasonmythtv-desktop
2009-05-13 05:35:04.102 New DB connection, total: 1
2009-05-13 05:35:04.108 Connected to database 'mythconverg' at host: localhost
2009-05-13 05:35:04.110 Closing DB connection named 'DBManager0'
2009-05-13 05:35:04.111 Connected to database 'mythconverg' at host: localhost
2009-05-13 05:35:04.113 New DB connection, total: 2
2009-05-13 05:35:04.116 Connected to database 'mythconverg' at host: localhost
2009-05-13 05:35:04.118 Current Schema Version: 1214
2009-05-13 05:35:04.124 Preview Error: Previewer file '/var/lib/mythtv/recordings/1111_20090513053501.mpg' is not valid.
2009-05-13 05:35:04.125 Preview Error: Run() file not local: '/var/lib/mythtv/recordings/1111_20090513053501.mpg'
2009-05-13 05:35:04.131 Preview Error: Preview process not ok.
            fileinfo(/var/lib/mythtv/recordings/1111_20090513053501.mpg.png) exists: 0 readable: 0 size: 0
2009-05-13 05:35:10.305 TVRec(8): HW Tuner: 8->8
2009-05-13 05:35:11.630 Finished recording CBS 11 News This Morning at 5AM: channel 1111
2009-05-13 05:35:11.683 Using runtime prefix = /usr
2009-05-13 05:35:11.688 Empty LocalHostName.
2009-05-13 05:35:11.689 Using localhost value of jasonmythtv-desktop
2009-05-13 05:35:11.694 New DB connection, total: 1
2009-05-13 05:35:11.698 Connected to database 'mythconverg' at host: localhost
2009-05-13 05:35:11.700 Closing DB connection named 'DBManager0'
2009-05-13 05:35:11.703 Connected to database 'mythconverg' at host: localhost
2009-05-13 05:35:11.705 New DB connection, total: 2
2009-05-13 05:35:11.707 Connected to database 'mythconverg' at host: localhost
2009-05-13 05:35:11.708 Current Schema Version: 1214
2009-05-13 05:35:11.770 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-05-13 05:35:11.815 DTVSM(0) Error: Wrong PMT; pmt->pn(3) desired(7)
2009-05-13 05:35:11.818 DTVSM(0) Error: Wrong PMT; pmt->pn(4) desired(7)
2009-05-13 05:35:11.826 DTVSM(0) Error: Wrong PMT; pmt->pn(5) desired(7)
2009-05-13 05:35:11.834 DTVSM(0) Error: Wrong PMT; pmt->pn(6) desired(7)
2009-05-13 05:35:11.850 DTVSM(0) Error: Wrong PMT; pmt->pn(8) desired(7)
2009-05-13 05:35:12.090 Finished recording CBS 11 News This Morning at 5AM: channel 2215
2009-05-13 05:35:13.109 Finished recording CBS 11 News This Morning at 5AM: channel 2215
2009-05-13 05:35:13.158 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-05-13 05:35:13.166 Using runtime prefix = /usr
2009-05-13 05:35:13.205 Empty LocalHostName.
2009-05-13 05:35:13.238 Using localhost value of jasonmythtv-desktop
2009-05-13 05:35:13.252 New DB connection, total: 1
2009-05-13 05:35:13.257 Connected to database 'mythconverg' at host: localhost
2009-05-13 05:35:13.263 Closing DB connection named 'DBManager0'
2009-05-13 05:35:13.272 Connected to database 'mythconverg' at host: localhost
2009-05-13 05:35:13.279 New DB connection, total: 2
2009-05-13 05:35:13.287 Connected to database 'mythconverg' at host: localhost
2009-05-13 05:35:13.295 Current Schema Version: 1214
2009-05-13 05:35:13.305 Preview Error: Previewer file '/var/lib/mythtv/recordings/2215_20090513053510.mpg' is not valid.
2009-05-13 05:35:13.311 Preview Error: Run() file not local: '/var/lib/mythtv/recordings/2215_20090513053510.mpg'
2009-05-13 05:35:13.323 Preview Error: Preview process not ok.
            fileinfo(/var/lib/mythtv/recordings/2215_20090513053510.mpg.png) exists: 0 readable: 0 size: 0
2009-05-13 05:35:14.211 AFD: Opened codec 0x270ca90, id(MPEG1VIDEO) type(Video)
2009-05-13 05:35:14.215 AFD: Opened codec 0x270cf70, id(MPEG2VIDEO) type(Video)
2009-05-13 05:35:14.217 AFD: codec AC3 has 6 channels
2009-05-13 05:35:14.219 AFD: Opened codec 0x270d5b0, id(AC3) type(Audio)
2009-05-13 05:35:19.108 Preview: Grabbed preview '/var/lib/mythtv/recordings/1111_20090513053502.mpg' 640x480@69s
2009-05-13 05:35:54.435 TVRec(8): HW Tuner: 8->8
2009-05-13 05:35:55.762 Finished recording CBS 11 News This Morning at 5AM: channel 2215
2009-05-13 05:35:55.815 Using runtime prefix = /usr
2009-05-13 05:35:55.827 Empty LocalHostName.
2009-05-13 05:35:55.828 Using localhost value of jasonmythtv-desktop
2009-05-13 05:35:55.833 New DB connection, total: 1
2009-05-13 05:35:55.837 Connected to database 'mythconverg' at host: localhost
2009-05-13 05:35:55.840 Closing DB connection named 'DBManager0'
2009-05-13 05:35:55.843 Connected to database 'mythconverg' at host: localhost
2009-05-13 05:35:55.847 New DB connection, total: 2
2009-05-13 05:35:55.848 Connected to database 'mythconverg' at host: localhost
2009-05-13 05:35:55.852 Current Schema Version: 1214
2009-05-13 05:35:55.970 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-05-13 05:35:56.184 DTVSM(0) Error: Wrong PMT; pmt->pn(3) desired(1)
2009-05-13 05:35:56.503 Finished recording CBS 11 News This Morning at 5AM: channel 1111
2009-05-13 05:35:57.526 Finished recording CBS 11 News This Morning at 5AM: channel 1111
2009-05-13 05:35:57.536 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-05-13 05:35:57.583 Using runtime prefix = /usr
2009-05-13 05:35:57.589 Empty LocalHostName.
2009-05-13 05:35:57.591 Using localhost value of jasonmythtv-desktop
2009-05-13 05:35:57.596 New DB connection, total: 1
2009-05-13 05:35:57.601 Connected to database 'mythconverg' at host: localhost
2009-05-13 05:35:57.607 Closing DB connection named 'DBManager0'
2009-05-13 05:35:57.615 Connected to database 'mythconverg' at host: localhost
2009-05-13 05:35:57.665 New DB connection, total: 2
2009-05-13 05:35:57.670 Connected to database 'mythconverg' at host: localhost
2009-05-13 05:35:57.680 Current Schema Version: 1214
2009-05-13 05:35:57.690 Preview Error: Previewer file '/var/lib/mythtv/recordings/1111_20090513053554.mpg' is not valid.
2009-05-13 05:35:57.695 Preview Error: Run() file not local: '/var/lib/mythtv/recordings/1111_20090513053554.mpg'
2009-05-13 05:35:57.708 Preview Error: Preview process not ok.
            fileinfo(/var/lib/mythtv/recordings/1111_20090513053554.mpg.png) exists: 0 readable: 0 size: 0
2009-05-13 05:35:58.374 AFD: Opened codec 0x13d6a90, id(MPEG2VIDEO) type(Video)
2009-05-13 05:35:58.379 AFD: codec AC3 has 2 channels
2009-05-13 05:35:58.381 AFD: Opened codec 0x13d6f70, id(AC3) type(Audio)
2009-05-13 05:35:58.411 Preview: Grabbed preview '/var/lib/mythtv/recordings/2215_20090513053512.mpg' 704x480@69s
2009-05-13 05:36:12.435 Expiring 0 MBytes for 1111 @ Wed May 13 05:00:00 2009 => CBS 11 News This Morning at 5AM
2009-05-13 05:36:12.441 Expiring 6 MBytes for 1111 @ Wed May 13 05:00:00 2009 => CBS 11 News This Morning at 5AM
2009-05-13 05:36:12.444 Expiring 0 MBytes for 2215 @ Wed May 13 05:00:00 2009 => CBS 11 News This Morning at 5AM
2009-05-13 05:36:44.563 TVRec(8): Changing from WatchingLiveTV to None
2009-05-13 05:36:44.822 Finished recording CBS 11 News This Morning at 5AM: channel 1111

==> /var/log/mythtv/mythfrontend.log <==
2009-05-13 05:34:52.254 Specified base font 'medium' does not exist for font large
2009-05-13 05:34:52.254 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-05-13 05:34:52.365 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-05-13 05:34:52.380 Registering Internal as a media playback plugin.
2009-05-13 05:34:52.551 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-05-13 05:34:52.782 MythMusic adding CD-Writer: 5,0,0 -- DVD-RAM GH22NS30
2009-05-13 05:34:52.783 MythMusic adding CD-Writer: 6,0,0 -- iHDP118   4     
2009-05-13 05:34:52.805 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.24.106:5060 NAT address 192.168.24.106
SIP: Cannot register; proxy, username or password not set
2009-05-13 05:34:52.874 No theme dir: /home/jasonmythtv/.mythtv/themes/Mythbuntu-8.04
2009-05-13 05:35:01.165 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-05-13 05:35:01.166 Using protocol version 40
2009-05-13 05:35:01.200 TV: Attempting to change from None to WatchingLiveTV
2009-05-13 05:35:01.201 Using protocol version 40
2009-05-13 05:35:02.602 DPMS Deactivated 
2009-05-13 05:35:02.606 New DB connection, total: 3
2009-05-13 05:35:02.606 Connected to database 'mythconverg' at host: localhost
2009-05-13 05:35:02.611 NVP: Disabling Audio, params(-1,2,44100)
2009-05-13 05:35:02.622 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-05-13 05:35:02.642 OSD Theme Dimensions W: 640 H: 480
2009-05-13 05:35:02.874 TV: Changing from None to WatchingLiveTV
2009-05-13 05:35:02.875 New DB connection, total: 4
2009-05-13 05:35:02.875 Connected to database 'mythconverg' at host: localhost
2009-05-13 05:35:02.876 Realtime priority would require SUID as root.
Initialize Yadif Deinterlacer. In-Pixformat = 1 Out-Pixformat=1
yadifdeint: size changed from 0 x 0 -> 720 x 576
2009-05-13 05:35:02.977 Video sync method can't support double framerate (refresh rate too low for bob deint)
Initialize Yadif Deinterlacer. In-Pixformat = 1 Out-Pixformat=1
yadifdeint: size changed from 0 x 0 -> 720 x 576
2009-05-13 05:35:02.979 Video timing method: USleep with busy wait
2009-05-13 05:35:06.019 NVP: Prebuffer wait timed out 10 times.
Initialize Yadif Deinterlacer. In-Pixformat = 1 Out-Pixformat=1
yadifdeint: size changed from 0 x 0 -> 640 x 480
2009-05-13 05:35:06.654 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-05-13 05:35:06.748 AFD: Opened codec 0x7f02f40ce9f0, id(MPEG2VIDEO) type(Video)
2009-05-13 05:35:06.749 AFD: Opened codec 0x7f02f46e3a40, id(MPEG2VIDEO) type(Video)
2009-05-13 05:35:06.749 AFD: codec AC3 has 6 channels
2009-05-13 05:35:06.750 AFD: Opened codec 0x7f02f40cc210, id(AC3) type(Audio)
2009-05-13 05:35:06.829 Opening audio device 'spdif'. ch 2(2) sr 48000
2009-05-13 05:35:06.829 Opening ALSA audio device 'spdif'.
2009-05-13 05:35:06.994 NVP: Enabling Audio
2009-05-13 05:35:07.717 NVP: Prebuffer wait timed out 10 times.
2009-05-13 05:35:09.051 NVP: Prebuffer wait timed out 10 times.
2009-05-13 05:35:10.386 NVP: Prebuffer wait timed out 10 times.
2009-05-13 05:35:13.590 NVP: Prebuffer wait timed out 10 times.
Initialize Yadif Deinterlacer. In-Pixformat = 1 Out-Pixformat=1
yadifdeint: size changed from 0 x 0 -> 704 x 480
2009-05-13 05:35:14.533 AFD: Opened codec 0x7f02f40ce9f0, id(MPEG2VIDEO) type(Video)
2009-05-13 05:35:14.533 AFD: codec AC3 has 2 channels
2009-05-13 05:35:14.533 AFD: Opened codec 0x7f02f46e3a40, id(AC3) type(Audio)
2009-05-13 05:35:36.364 DPMS Reactivated.
2009-05-13 05:35:43.435 DPMS Deactivated 
2009-05-13 05:35:58.157 WriteAudio: buffer underrun
2009-05-13 05:35:59.478 NVP: Prebuffer wait timed out 10 times.
Initialize Yadif Deinterlacer. In-Pixformat = 1 Out-Pixformat=1
yadifdeint: size changed from 0 x 0 -> 640 x 480
2009-05-13 05:36:00.595 AFD: Opened codec 0x1851110, id(MPEG2VIDEO) type(Video)
2009-05-13 05:36:00.596 AFD: Opened codec 0x2857820, id(MPEG2VIDEO) type(Video)
2009-05-13 05:36:00.596 AFD: codec AC3 has 6 channels
2009-05-13 05:36:00.597 AFD: Opened codec 0x1686da0, id(AC3) type(Audio)
2009-05-13 05:36:00.808 NVP: Prebuffer wait timed out 10 times.
2009-05-13 05:36:02.139 NVP: Prebuffer wait timed out 10 times.
2009-05-13 05:36:03.469 NVP: Prebuffer wait timed out 10 times.
2009-05-13 05:36:04.799 NVP: Prebuffer wait timed out 10 times.
2009-05-13 05:36:06.129 NVP: Prebuffer wait timed out 10 times.
2009-05-13 05:36:07.459 NVP: Prebuffer wait timed out 10 times.
2009-05-13 05:36:08.790 NVP: Prebuffer wait timed out 10 times.
2009-05-13 05:36:10.120 NVP: Prebuffer wait timed out 10 times.
2009-05-13 05:36:11.450 NVP: Prebuffer wait timed out 10 times.
2009-05-13 05:36:12.780 NVP: Prebuffer wait timed out 10 times.
2009-05-13 05:36:14.111 NVP: Prebuffer wait timed out 10 times.
2009-05-13 05:36:15.441 NVP: Prebuffer wait timed out 10 times.
2009-05-13 05:36:16.771 NVP: Prebuffer wait timed out 10 times.
2009-05-13 05:36:18.101 NVP: Prebuffer wait timed out 10 times.
2009-05-13 05:36:19.431 NVP: Prebuffer wait timed out 10 times.
2009-05-13 05:36:20.762 NVP: Prebuffer wait timed out 10 times.
2009-05-13 05:36:22.092 NVP: Prebuffer wait timed out 10 times.
2009-05-13 05:36:23.422 NVP: Prebuffer wait timed out 10 times.
2009-05-13 05:36:24.752 NVP: Prebuffer wait timed out 10 times.
2009-05-13 05:36:26.083 NVP: Prebuffer wait timed out 10 times.
2009-05-13 05:36:27.413 NVP: Prebuffer wait timed out 10 times.
2009-05-13 05:36:28.743 NVP: Prebuffer wait timed out 10 times.
2009-05-13 05:36:30.073 NVP: Prebuffer wait timed out 10 times.
2009-05-13 05:36:31.404 NVP: Prebuffer wait timed out 10 times.
2009-05-13 05:36:32.734 NVP: Prebuffer wait timed out 10 times.
2009-05-13 05:36:34.064 NVP: Prebuffer wait timed out 10 times.
2009-05-13 05:36:35.395 NVP: Prebuffer wait timed out 10 times.
2009-05-13 05:36:36.725 NVP: Prebuffer wait timed out 10 times.
2009-05-13 05:36:38.055 NVP: Prebuffer wait timed out 10 times.
2009-05-13 05:36:39.385 NVP: Prebuffer wait timed out 10 times.
2009-05-13 05:36:40.716 NVP: Prebuffer wait timed out 10 times.
2009-05-13 05:36:42.046 NVP: Prebuffer wait timed out 10 times.
2009-05-13 05:36:43.376 NVP: Prebuffer wait timed out 10 times.
2009-05-13 05:36:44.507 TV: Attempting to change from WatchingLiveTV to None
2009-05-13 05:36:44.706 NVP: Prebuffer wait timed out 10 times.
2009-05-13 05:36:44.839 TV: Changing from WatchingLiveTV to None
2009-05-13 05:36:44.907 DPMS Reactivated.
Destroying SipFsm object 
2009-05-13 05:36:51.854 Deleting UPnP client...

---

### Post by klc5555 on 2009-05-13
Well, clearly a backend problem of some sort with this particular channel, but one beyond my level of expertise in myth and tuner cards. At this point I'd probably try to build a channels.conf file using dvbapps and see whether myth or some other simpler tv viewer can tune this channel when its specifications are loaded from such a file.

But hopefully a developer or someone with real knowledge in this area will weigh in.

---

### Post by epi 1:10,000 on 2009-05-18
I did a fresh install of Mythbuntu 9.04_x86_64 (previously had 8.10_x86_64) and I still have the same problem w/ CBS.  Did CBS/Time Warner embed CGMS-A into their stream in Dallas?
No live TV or recording playback in the frontend but I can playback the recorded file in Mythbuntu gnome desktop in mPlayer but it breaks my audio.

Could it be Like this problem? [http://www.gossamer-threads.com/lists/mythtv/dev/381059](http://www.gossamer-threads.com/lists/mythtv/dev/381059)

---

### Post by epi 1:10,000 on 2009-05-19
Can anyone confirm if  this is this the same problem as [http://svn.mythtv.org/trac/ticket/3640#comment:48](http://svn.mythtv.org/trac/ticket/3640#comment:48) ?????    Has anyone had a similar problem W/ DVB-C in the USA?

---

### Post by AboveTheLogic on 2009-05-20
Have you ever been to AVSForums? In their HDTV section they have specific threads for different locals. You could probably tell if this is a problem specific to you or among others by visiting and/or posting in the right thread.

Alternatively, you could try to use another type of QAM tuner, perhaps one that may be built into a TV you might have...

---

### Post by epi 1:10,000 on 2009-07-01
I rescanned after the digital transition and now I receive CBS via QAM.  Never was able to figure out why but it may have been because of the TWC was rebroadcasting it causing it to be identified as MPEG1VIDEO.

[FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black][FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black]"The misdetection of the 0x1986 stream as MPEG1VIDEO is the problem. 
Because it is listed before the real video stream (0x1984) in the PMT, 
MythTV is choosing it and then never finding any actual video frames."[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT] - [FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black][FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black]David Engel[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]

---

