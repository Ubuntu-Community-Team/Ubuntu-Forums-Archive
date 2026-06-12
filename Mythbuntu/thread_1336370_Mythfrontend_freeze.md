---
title: "Mythfrontend freeze"
date: 2009-11-24
forum: Mythbuntu
---

### Post by orduek on 2009-11-24
Hi,
I'm using Mythbuntu 9.04 with VDPAU high quality playback profile.
I have Nvidia 9400GT.
recently I encounter a problem while watching LiveTV. once in a while the frontend freezes. 
I tried a few playback profiles to no vail.
I attach my frontend and backend logs in a hope somone could tell me what is happening. 
thank you.

Mythfrontend log (I attach near time of freezing):
```
2009-11-24 20:05:33.713 [h264_vdpau @ 0xb6c167c0]number of reference frames exceeds max (probably corrupt input), discarding one
2009-11-24 20:05:33.713 [h264_vdpau @ 0xb6c167c0]number of reference frames exceeds max (probably corrupt input), discarding one
2009-11-24 20:05:33.713 [h264_vdpau @ 0xb6c167c0]number of reference frames exceeds max (probably corrupt input), discarding one
2009-11-24 20:05:33.713 [h264_vdpau @ 0xb6c167c0]number of reference frames exceeds max (probably corrupt input), discarding one
2009-11-24 20:05:33.713 [h264_vdpau @ 0xb6c167c0]number of reference frames exceeds max (probably corrupt input), discarding one
2009-11-24 20:05:33.713 [h264_vdpau @ 0xb6c167c0]number of reference frames exceeds max (probably corrupt input), discarding one
2009-11-24 20:05:33.713 [h264_vdpau @ 0xb6c167c0]number of reference frames exceeds max (probably corrupt input), discarding one
2009-11-24 20:05:33.713 [h264_vdpau @ 0xb6c167c0]mmco: unref short failure
2009-11-24 20:05:33.728 [h264_vdpau @ 0xb6c167c0]mmco: unref short failure
2009-11-24 20:05:33.748 [h264_vdpau @ 0xb6c167c0]mmco: unref short failure
2009-11-24 20:05:33.801 WriteAudio: buffer underrun
2009-11-24 20:05:53.398 NVP(5): prebuffering pause
2009-11-24 20:06:13.638 [h264_vdpau @ 0xb6c167c0]illegal short term buffer state detected
2009-11-24 20:14:29.348 NVP(5): prebuffering pause
2009-11-24 20:14:31.008 NVP(5): Prebuffer wait timed out 10 times.
2009-11-24 20:14:32.673 NVP(5): Prebuffer wait timed out 20 times.
2009-11-24 20:14:34.339 NVP(5): Prebuffer wait timed out 30 times.
2009-11-24 20:14:36.005 NVP(5): Prebuffer wait timed out 40 times.
2009-11-24 20:14:37.671 NVP(5): Prebuffer wait timed out 50 times.
2009-11-24 20:14:39.219 TV: Attempting to change from Watching WatchingLiveTV to None
2009-11-24 20:14:39.337 NVP(5): Prebuffer wait timed out 60 times.
2009-11-24 20:14:39.345 TV: Changing from Watching WatchingLiveTV to None
2009-11-24 20:14:39.346 ScreenSaverX11Private: DPMS Reactivated 1
2009-11-24 20:14:41.003 NVP(5): Prebuffer wait timed out 70 times.
2009-11-24 20:14:42.669 NVP(5): Prebuffer wait timed out 80 times.
2009-11-24 20:14:44.335 NVP(5): Prebuffer wait timed out 90 times.
2009-11-24 20:14:46.000 NVP(5): Prebuffer wait timed out 100 times.
2009-11-24 20:14:46.000 NVP(5), Error: Timed out waiting for prebuffering too long. Exiting..
2009-11-24 20:14:47.666 NVP(5): Prebuffer wait timed out 110 times.
2009-11-24 20:14:47.666 NVP(5), Error: Timed out waiting for prebuffering too long. Exiting..
2009-11-24 20:14:47.666 NVP(5), Error: Video frame buffering failed too many times.
2009-11-24 20:14:49.332 NVP(5): Prebuffer wait timed out 120 times.
2009-11-24 20:14:49.332 NVP(5), Error: Timed out waiting for prebuffering too long. Exiting..
2009-11-24 20:14:49.332 NVP(5), Error: Video frame buffering failed too many times.
2009-11-24 20:14:50.998 NVP(5): Prebuffer wait timed out 130 times.
2009-11-24 20:14:50.998 NVP(5), Error: Timed out waiting for prebuffering too long. Exiting..
2009-11-24 20:14:50.998 NVP(5), Error: Video frame buffering failed too many times.
2009-11-24 20:14:52.664 NVP(5): Prebuffer wait timed out 140 times.
2009-11-24 20:14:52.664 NVP(5), Error: Timed out waiting for prebuffering too long. Exiting..
2009-11-24 20:14:52.664 NVP(5), Error: Video frame buffering failed too many times.
2009-11-24 20:14:54.330 NVP(5): Prebuffer wait timed out 150 times.
2009-11-24 20:14:54.330 NVP(5), Error: Timed out waiting for prebuffering too long. Exiting..
2009-11-24 20:14:54.330 NVP(5), Error: Video frame buffering failed too many times.
2009-11-24 20:14:55.996 NVP(5): Prebuffer wait timed out 160 times.
2009-11-24 20:14:55.996 NVP(5), Error: Timed out waiting for prebuffering too long. Exiting..
2009-11-24 20:14:55.996 NVP(5), Error: Video frame buffering failed too many times.
2009-11-24 20:14:57.661 NVP(5): Prebuffer wait timed out 170 times.
2009-11-24 20:14:57.662 NVP(5), Error: Timed out waiting for prebuffering too long. Exiting..
2009-11-24 20:14:57.662 NVP(5), Error: Video frame buffering failed too many times.
2009-11-24 20:14:59.327 NVP(5): Prebuffer wait timed out 180 times.
2009-11-24 20:14:59.327 NVP(5), Error: Timed out waiting for prebuffering too long. Exiting..
2009-11-24 20:14:59.327 NVP(5), Error: Video frame buffering failed too many times.
2009-11-24 20:15:00.993 NVP(5): Prebuffer wait timed out 190 times.
2009-11-24 20:15:00.993 NVP(5), Error: Timed out waiting for prebuffering too long. Exiting..
2009-11-24 20:15:00.993 NVP(5), Error: Video frame buffering failed too many times.
2009-11-24 20:15:02.659 NVP(5): Prebuffer wait timed out 200 times.
2009-11-24 20:15:02.659 NVP(5), Error: Timed out waiting for prebuffering too long. Exiting..
2009-11-24 20:15:02.659 NVP(5), Error: Video frame buffering failed too many times.
2009-11-24 20:15:04.325 NVP(5): Prebuffer wait timed out 210 times.
2009-11-24 20:15:04.325 NVP(5), Error: Timed out waiting for prebuffering too long. Exiting..
2009-11-24 20:15:04.325 NVP(5), Error: Video frame buffering failed too many times.
2009-11-24 20:15:05.991 NVP(5): Prebuffer wait timed out 220 times.
2009-11-24 20:15:05.991 NVP(5), Error: Timed out waiting for prebuffering too long. Exiting..
2009-11-24 20:15:05.991 NVP(5), Error: Video frame buffering failed too many times.
2009-11-24 20:15:07.657 NVP(5): Prebuffer wait timed out 230 times.
2009-11-24 20:15:07.657 NVP(5), Error: Timed out waiting for prebuffering too long. Exiting..
2009-11-24 20:15:07.657 NVP(5), Error: Video frame buffering failed too many times.
2009-11-24 20:15:09.322 NVP(5): Prebuffer wait timed out 240 times.
2009-11-24 20:15:09.323 NVP(5), Error: Timed out waiting for prebuffering too long. Exiting..
2009-11-24 20:15:09.323 NVP(5), Error: Video frame buffering failed too many times.
2009-11-24 20:15:10.988 NVP(5): Prebuffer wait timed out 250 times.
2009-11-24 20:15:10.988 NVP(5), Error: Timed out waiting for prebuffering too long. Exiting..
2009-11-24 20:15:10.988 NVP(5), Error: Video frame buffering failed too many times.
2009-11-24 20:15:12.654 NVP(5): Prebuffer wait timed out 260 times.
2009-11-24 20:15:12.654 NVP(5), Error: Timed out waiting for prebuffering too long. Exiting..
2009-11-24 20:15:12.654 NVP(5), Error: Video frame buffering failed too many times.
2009-11-24 20:15:14.320 NVP(5): Prebuffer wait timed out 270 times.
2009-11-24 20:15:14.320 NVP(5), Error: Timed out waiting for prebuffering too long. Exiting..
2009-11-24 20:15:14.320 NVP(5), Error: Video frame buffering failed too many times.
2009-11-24 20:15:15.986 NVP(5): Prebuffer wait timed out 280 times.
2009-11-24 20:15:15.986 NVP(5), Error: Timed out waiting for prebuffering too long. Exiting..
2009-11-24 20:15:15.986 NVP(5), Error: Video frame buffering failed too many times.
2009-11-24 20:15:17.668 NVP(5): Prebuffer wait timed out 290 times.
2009-11-24 20:15:17.669 NVP(5), Error: Timed out waiting for prebuffering too long. Exiting..
2009-11-24 20:15:17.669 NVP(5), Error: Video frame buffering failed too many times.
2009-11-24 20:15:19.667 NVP(5): Prebuffer wait timed out 300 times.
2009-11-24 20:15:19.668 NVP(5), Error: Timed out waiting for prebuffering too long. Exiting..
2009-11-24 20:15:19.668 NVP(5), Error: Video frame buffering failed too many times.
2009-11-24 20:15:21.333 NVP(5): Prebuffer wait timed out 310 times.
2009-11-24 20:15:21.333 NVP(5), Error: Timed out waiting for prebuffering too long. Exiting..
2009-11-24 20:15:21.333 NVP(5), Error: Video frame buffering failed too many times.
```

Mythbackend log (same here, near time of freezing):
```
2009-11-24 20:00:02.332 [h264 @ 0xb6d927c0]number of reference frames exceeds max (probably corrupt input), discarding one
2009-11-24 20:00:02.334 [h264 @ 0xb6d927c0]number of reference frames exceeds max (probably corrupt input), discarding one
2009-11-24 20:00:02.335 [h264 @ 0xb6d927c0]number of reference frames exceeds max (probably corrupt input), discarding one
2009-11-24 20:00:02.337 [h264 @ 0xb6d927c0]number of reference frames exceeds max (probably corrupt input), discarding one
2009-11-24 20:00:02.343 [h264 @ 0xb6d927c0]mmco: unref short failure
2009-11-24 20:00:02.351 [h264 @ 0xb6d927c0]mmco: unref short failure
2009-11-24 20:00:02.369 [h264 @ 0xb6d927c0]mmco: unref short failure
2009-11-24 20:00:02.460 Preview: Grabbed preview '/var/lib/mythtv/livetv/3002_20091124195930.mpg' 720x576@64s
2009-11-24 20:00:03.039 TVRec(7): RingBufferChanged()
2009-11-24 20:00:03.048 Finished recording     (' ): channel 3002
2009-11-24 20:00:05.276 RecBase(7:/dev/dvb/adapter0/frontend0): GetKeyframePositions(1,9223372036854775807,#0) out of 1
2009-11-24 20:02:43.020 Expiring 0 MBytes for 3002 @ Tue Nov 24 19:00:00 2009 =>     (' )
2009-11-24 20:02:43.022 Expiring 8 MBytes for 3002 @ Tue Nov 24 19:00:00 2009 =>     (' )
2009-11-24 20:05:33.097 RecBase(7:/dev/dvb/adapter0/frontend0): GetKeyframePositions(8115,9223372036854775807,#3) out of 247
2009-11-24 20:14:39.241 TVRec(7): Changing from Watching WatchingLiveTV to None
2009-11-24 20:14:39.247 Unknown type, recording width was 720
2009-11-24 20:14:39.342 Finished recording  10  (' ): channel 3002
2009-11-24 20:14:43.048 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-11-24 20:14:43.057 Expiring 58 MBytes for 3003 @ Mon Nov 23 19:30:00 2009 =>     
2009-11-24 20:17:01.664 MainServer::ANN Monitor
2009-11-24 20:17:01.672 adding: HTPC as a client (events: 0)
```

---

### Post by orduek on 2009-12-12
any one has idea how can I solve this one?
It happens when I use the DVB-T card and not when using the analog one.

---

### Post by matt06 on 2009-12-12
Looks like it could be signal or driver issue.  Have you checked dmesg or any other backend logs after it freezes?

EDIT:  actually, after googling it looks to be a frontend/vdpau problem, not backend.

Edit2:  some links.  ffmpeg bug, but supposed to be fixed soon?

[VDPAU: dealing with corrupt streams]("http://www.nvnews.net/vbulletin/showthread.php?t=127442")

[Nova-hd-s2 video stuttering.]("http://ubuntuforums.org/showthread.php?t=1322669")

---

### Post by orduek on 2009-12-13
Ok,
I noticed that the frontend freeze happens when the show is coming back from commercials.
what it means?
can I change some setting regarding commercials and enjoy liveTV until the bug is fixed?

---

### Post by orduek on 2009-12-18
any change on this subject?

---

### Post by NightStorm on 2009-12-18
I cannot contribute anything to this, other than I saw your subject line and was interested to see if I could learn anything about avoiding front-end freezes.  I've been using MythTV since last March starting at 8.10, then 9.04, and now 9.10 and have found it throughout to be quite fragile, freezing being just many one of the ways that it can fail.  Nonetheless I keep fiddling with it because, well, it is just a lot of fun.  :)

---

### Post by matt06 on 2009-12-20
Hello orduek.

Have you tried different playback profiles?  Does it still freeze if you turn off commercial skip?  Also you can try external players such as mplayer or tvtime I believe to see if those are affected as well.

Sorry I can't be of more help.

---

### Post by orduek on 2009-12-20
Thanks-
I think I disabled commercial skip but I'm not sure.
can you please tell me were it is?

---

### Post by matt06 on 2009-12-20
You can turn off commercial skip during playback using the menu.  Or to turn it off permanently go to Setup, TV Settings, Playback, then next to Commercial Skip (8/9).  This is on Mythbuntu 9.10 with MythCenter theme so your menus may vary.

---

### Post by movieman on 2009-12-20
BTW, you're not the only one getting this, I mentioned this problem here a couple of weeks ago. The frontend seems to get into this 'Timed out waiting for prebuffering too long' state and never, ever gets out of it until I kill it.

---

### Post by orduek on 2009-12-21
I found this bug report:
[http://svn.mythtv.org/trac/ticket/7041](http://svn.mythtv.org/trac/ticket/7041)

Hope they'll fix it soon.
mean while I'm trying to avoid the frames coming back from commercials (It always freezes when the commercials end and the show begins).
A bit ridiculous but what can you do?

---

### Post by radnor on 2009-12-21
I have frontend freeze too.  But, I do not know if it is just FE freeze or DESKTOP freeze. 

My setup:  BE/FE P4. 80G IDE system disk.  500G /VAR connected via PCI SATA controller.  My BE/FE will freeze.

I had it freeze while playing a ripped movie (this AM about 10 minutes into it).  I've ripped a DVD then let it sit and a freeze would occur (after rip).  I've had it on the desktop and freeze.

When it is frozen, the BE works just fine!  I can ping and ssh into the BE.  A RFE can (and will) keep playing just as happy as can be...

Other than this problem, it's great.

Both systems are running 9.10 mythbuntu

---

### Post by dad311 on 2009-12-21
Ive got the same issue, what a bummer.  Hope its fixed soon.

---

### Post by orduek on 2010-01-12
any progress on this issue?

---

### Post by orduek on 2010-01-19
Is there someone who knows if there's a chance of progress in this area?
It really annoying :(

---

### Post by radnor on 2010-01-19
I only have this problem on a BE/FE system.  I want to use it for a BE only and put the system somewhere else in my house once I have it set up the way I want.

I do NOT have this issue with a RFE.  But, a soultion would be great too.

I noticed (think) it may not be a FE freeze, but a DESKTOP freeze.  I had a lock up on the FE, Desktop, login, etc.  However, the BE keeps on working!

---

### Post by orduek on 2010-01-23
Does anyone that did clean installation of Mythbuntu 9.10 suffer from this problem?
I'm thinking maybe thats the solution for me but its a lot of work to backup and upgrade my system with a clean installation.
any suggestions?

---

### Post by orduek on 2010-01-26
OK, I did a clean installation of mythbuntu 9.10, added the avenard repo's and...same thing :(
It still freezes, on a specific channel (not the other ones), usually when going back from commercials.

---

### Post by orduek on 2010-01-31
does someone knows if there's something to be done about it? 
its really frustrating.

---

### Post by cheway on 2010-02-13
I'm getting the same problem, but I am running a LinuxMCE Media Director in VirtualBox in Karmic. I really hope this gets sorted, it's doing my head in.

---

### Post by wombo on 2010-05-29
Are there any updates to this I am always crashing when I return from an ad skip.

To me it only seems to be on some channels and I also suspect it is only high def shows.




(Recording using HDHR DVB-T)

Frontend Logs: [http://pastebin.com/myixGNj2](http://pastebin.com/myixGNj2)

---

### Post by dlinvill on 2010-06-14
I started getting these errors on fast forward when I followed the dynamic refresh rate instruction described [URL="http://www.gossamer-threads.com/lists/mythtv/users/439398"]here: 
http://www.gossamer-threads.com/lists/mythtv/users/439398
[/URL]

Once I turned the separate video modes options back off the problem seemed to go away.  I have a hunch the trigger was commercials playing at a different rate than the show and fast forwarding through them with the multiple rate switches involved.

---

