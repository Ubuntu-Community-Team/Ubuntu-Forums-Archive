---
title: "LiveTV not working, pauses instead of playing"
date: 2008-12-18
forum: Mythbuntu
---

### Post by bretcb on 2008-12-18
Hopefully someone can point me in the right direction with this.  I've done a lot of searching on this forum and google without finding any clues so far.  If this has been answered I apologise for not having been able to use the right keywords to find it

I've just installed a Mythbuntu 8.10 system.  It's a P4 3.0GHz hyperthreaded machine, 1GB PC3200 400MHz RAM, a 120GB PATA system drive, a 1.5TB SATA drive (with the Seagate firmware update) on which /var is mounted (for the recordings, videos, music, etc.), an ATI 256MB video card (can't recall the model right now; 9600 maybe? The system is at work in my lab), a PVR-500 tuner, and I'm using the onboard audio on an Asus P800D motherboard.

I've managed to slog through a few functionality problems, videos are playing, I have audio, etc.

The problem now is LiveTV.  I hooked up a GameCube to the composite inputs (only video-playing device available to test with) with no game, just setup screen.  When I click "Watch TV", I see the video momentarily, but then it seems to pause.  When I hit fast forward, it will fast forward through the buffered video until it reaches the live point, then seem to pause again.  The OSD goes from crisp during the fast forward to choppy, and the video pauses.  If I hit fast forward again, the whole process repeats.  At 3x fast forward, it never seems to catch up to the "live" point; it just fast forwards ad nauseum.  At 5x, it eventually catches up.

Suggestions?  Ideas?  Should I try to find a more standard input, like a DVD player (and, if so, why?  shouldn't all composite inputs be equal?)  Any comments would be appreciated.

---

### Post by volkswagner on 2008-12-18
You should start by examining the logs.

/var/log/mythtv/mythfrontend.log
/Var/log/mythtv/mythbackend.log

Are you using the restricted drivers?

Have you tried the various playback profiles?

All hardware configurations create unique playback requirements.  This makes it difficult to recommend a setting.  Take notice you are viewing SD content, so pay attention to the settings in the 480x640 range.

Trying the four or five preset ones will give you a start.

When the OSD is choppy, changing the deinterlacer usually helps, for me this is "linearBlend".

---

### Post by ! ! ! winner on 2008-12-18
> **volkswagner said:**
> You should start by examining the logs.

/var/log/mythtv/mythfrontend.log
/Var/log/mythtv/mythbackend.log

Are you using the restricted drivers?

Have you tried the various playback profiles?

All hardware configurations create unique playback requirements.  This makes it difficult to recommend a setting.  Take notice you are viewing SD content, so pay attention to the settings in the 480x640 range.

Trying the four or five preset ones will give you a start.

When the OSD is choppy, changing the deinterlacer usually helps, for me this is "linearBlend".


[http://www.prizerebel.com/index.php?r=806574](http://www.prizerebel.com/index.php?r=806574) come here  freethings!!!!!!!!!! no scam

---

### Post by bretcb on 2008-12-18
Sorry I couldn't get back to this earlier; busy day today

> **volkswagner said:**
> You should start by examining the logs.

/var/log/mythtv/mythfrontend.log

```
2008-12-18 16:35:45.512 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-12-18 16:35:45.514 Using protocol version 40
2008-12-18 16:35:45.687 TV: Attempting to change from None to WatchingLiveTV
2008-12-18 16:35:45.688 Using protocol version 40
2008-12-18 16:35:48.176 New DB connection, total: 3
2008-12-18 16:35:48.176 Connected to database 'mythconverg' at host: localhost
2008-12-18 16:35:48.210 DPMS Deactivated 
2008-12-18 16:35:49.070 AFD: Opened codec 0x8acf6e0, id(MPEG2VIDEO) type(Video)
2008-12-18 16:35:49.070 AFD: codec MP2 has 2 channels
2008-12-18 16:35:49.070 AFD: Opened codec 0x8aac3f0, id(MP2) type(Audio)
2008-12-18 16:35:49.102 Opening audio device 'default'. ch 2(2) sr 48000
2008-12-18 16:35:49.102 Opening ALSA audio device 'default'.
2008-12-18 16:35:49.252 VideoOutputXv: Desired video renderer 'ivtv' not available.
			codec 'MPEG2' makes 'xv-blit,xshm,opengl,xlib,' available, using 'xv-blit' instead.
2008-12-18 16:35:49.263 VideoOutputXv Error: Could not find suitable XVideo surface.
2008-12-18 16:35:49.264 VideoOutputXv: Falling back to X11 video output over a network socket.
			      *** May be very slow ***
2008-12-18 16:35:49.264 VideoOutputXv Error: XCreateImage failed: XJ_disp(0x9015d78) visual(0x901cca0) 
                        XJ_depth(24) WxH(1280x1024) bpl(3840)
2008-12-18 16:35:49.264 VideoOutputXv Error: Failed to create X buffers.
2008-12-18 16:35:49.566 Couldn't load deinterlace filter 
2008-12-18 16:35:49.571 OSD Theme Dimensions W: 640 H: 480
2008-12-18 16:35:50.178 TV: Changing from None to WatchingLiveTV
2008-12-18 16:35:50.181 Realtime priority would require SUID as root.
2008-12-18 16:35:50.182 FilterManager: failed to load filter 'none', no such filter exists
2008-12-18 16:35:50.182 Couldn't load deinterlace filter none
2008-12-18 16:35:50.185 Video timing method: USleep with busy wait
2008-12-18 16:35:53.595 WriteAudio: buffer underrun
   [... a whole bunch of these ... ]
2008-12-18 16:36:11.359 WriteAudio: buffer underrun
2008-12-18 16:36:11.457 TV: Attempting to change from WatchingLiveTV to None
2008-12-18 16:36:11.983 TV: Changing from WatchingLiveTV to None
2008-12-18 16:36:11.991 DPMS Reactivated.
```

> **volkswagner said:**
> /Var/log/mythtv/mythbackend.log

```
2008-12-18 16:35:45.526 MainServer::HandleAnnounce Monitor
2008-12-18 16:35:45.559 adding: BretCB-M01 as a client (events: 0)
2008-12-18 16:35:45.601 MainServer::HandleAnnounce Monitor
2008-12-18 16:35:45.642 adding: BretCB-M01 as a client (events: 1)
2008-12-18 16:35:45.689 MainServer::HandleAnnounce Playback
2008-12-18 16:35:45.742 adding: BretCB-M01 as a client (events: 0)
2008-12-18 16:35:45.798 TVRec(3): Changing from None to WatchingLiveTV
2008-12-18 16:35:45.837 TVRec(3): HW Tuner: 3->3
2008-12-18 16:35:45.882 Channel(/dev/video0) Warning: You have not set an external channel changing
			script for a composite or s-video input. Channel changing will do nothing.
2008-12-18 16:35:47.040 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2008-12-18 16:35:47.045 MPEGRec(/dev/video0) Warning: Audio sample rate 32000 Hz
			is not supported by ivtv driver, using 48000 Hz instead.
 *********************** WARNING ***********************
 ivtv drivers prior to 0.10.0 can cause lockups when    
 reading VBI. Drivers between 0.10.5 and 1.0.3+ do not  
 properly capture VBI data on PVR-250 and PVR-350 cards.

2008-12-18 16:36:11.495 TVRec(3): Changing from WatchingLiveTV to None
2008-12-18 16:36:11.909 Finished recording Unknown: channel 1001
2008-12-18 16:38:01.876 Expiring 14 MBytes for 1001 @ Thu Dec 18 16:35:45 2008 => Unknown
```

> **volkswagner said:**
> Are you using the restricted drivers?
Yes

> **volkswagner said:**
> Have you tried the various playback profiles?
I have now; it seems to make no difference.

> **volkswagner said:**
> When the OSD is choppy, changing the deinterlacer usually helps, for me this is "linearBlend".
Forgive what may be an obvious question, but, where do I find the deinterlacer settings?

---

### Post by azzer1234 on 2008-12-19
I have just been setting up the same release, mythbuntu 8.10 on a similar spec system, same processor, memory, 2 * analogue tuners and an ATI card. My live TV exhibited the same symptoms you described. I removed the restricted ATI graphics drivers and fell back to the ubuntu distributed and live TV works really well. Everything working really well. (I noted you were using restricted drivers).

---

### Post by bretcb on 2008-12-19
> **azzer1234 said:**
> I have just been setting up the same release, mythbuntu 8.10 on a similar spec system, same processor, memory, 2 * analogue tuners and an ATI card. My live TV exhibited the same symptoms you described. I removed the restricted ATI graphics drivers and fell back to the ubuntu distributed and live TV works really well. Everything working really well. (I noted you were using restricted drivers).

That did it.  I never thought of that, because I switched to them right after installing the system, because it recommended I do so.

> **volkswagner said:**
> Have you tried the various playback profiles?

This fixed a bunch of the other errors that were showing up in the logs, like the ivtv not being available error.  I'm still getting a few "WriteAudio: buffer underrun" errors, but even they're reduced dramatically

---

