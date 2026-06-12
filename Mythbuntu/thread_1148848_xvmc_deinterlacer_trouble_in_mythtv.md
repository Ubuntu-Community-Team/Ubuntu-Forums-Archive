---
title: "xvmc deinterlacer trouble in mythtv"
date: 2009-05-04
forum: Mythbuntu
---

### Post by ctcarroll on 2009-05-04
I have an AMD X2, 2GB RAM with a 7300GS.  Using nvidia proprietary driver version 180.44
If I use XvMC, Myth freezes after a few seconds of playback, sometimes locking up the whole machine.

I tracked through this thread and found it extremely helpful.  [http://ubuntuforums.org/showthread.php?t=1080988&highlight=AFD+Error%3A+Unknown+decoding+error]("http://ubuntuforums.org/showthread.php?t=1080988&highlight=AFD+Error%3A+Unknown+decoding+error")
I believe I have all settings matching, but I noticed an error message about the renderer that I think is the problem.  Not sure how to fix it though.   I'm using the default OSD, which has a blue band on the bottom, so I think that XvMC is not working.  I created a separate playback profile to use just XvMC at all resolutions.  Using standard xvmc decoder and xvmc-blit, 1CPU, bob 2x deinterlacer, and one field fallback deinterlacer.

I just upgraded to Jaunty, but I've actually been having this problem for a few months.

Below is the output from mythfrontend
2009-05-04 15:27:35.208 No theme dir: /home/john/.mythtv/themes/MythCenter
2009-05-04 15:28:18.384 edit #0 rejected
2009-05-04 15:28:37.697 New DB connection, total: 3
2009-05-04 15:28:37.698 Connected to database 'mythconverg' at host: localhost
2009-05-04 15:28:37.823 Received a remote 'Clear Cache' request
2009-05-04 15:28:49.270 TV: Attempting to change from None to WatchingLiveTV
2009-05-04 15:28:49.272 Using protocol version 40
2009-05-04 15:28:51.008 DPMS Deactivated 
2009-05-04 15:28:51.359 NVP: Disabling Audio, params(-1,2,44100)
2009-05-04 15:28:51.491 VideoOutputXv: Desired video renderer 'xvmc-blit' not available.
			codec 'None' makes 'xv-blit,xshm,opengl,xlib,' available, using 'xv-blit' instead.
2009-05-04 15:28:51.499 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-05-04 15:28:51.569 VideoOutputXv: Ack! Disabling ChromaKey OSD
			We can't use ChromaKey OSD if chromakeying is not supported!
2009-05-04 15:28:51.601 OSD Theme Dimensions W: 640 H: 480
2009-05-04 15:28:52.345 TV: Changing from None to WatchingLiveTV
2009-05-04 15:28:52.362 Using realtime priority.
2009-05-04 15:28:52.450 Video timing method: USleep with busy wait
2009-05-04 15:28:54.109 VideoOutputXv: XvMC Adaptor Name: 'NV17 Video Texture'
2009-05-04 15:28:54.125 VideoOutputXv: Ack! Disabling ChromaKey OSD
			We can't use ChromaKey OSD if chromakeying is not supported!
2009-05-04 15:28:54.132 VideoOutputXv: XvMC Adaptor Name: 'NV17 Video Texture'
2009-05-04 15:28:54.458 VideoOutputXv: ProcessFrameXvMC: Tried to reuse frame but failed
2009-05-04 15:28:54.458 VideoOutputXv: ProcessFrameXvMC: Called without frame
2009-05-04 15:28:54.474 AFD: Opened codec 0xa549010, id(MPEG2VIDEO_XVMC) type(Video)
2009-05-04 15:28:54.474 AFD: codec AC3 has 6 channels
2009-05-04 15:28:54.476 AFD: Opened codec 0xa5dd2d0, id(AC3) type(Audio)
2009-05-04 15:28:54.476 AFD: codec AC3 has 1 channels
2009-05-04 15:28:54.477 AFD: Opened codec 0x9fa0e40, id(AC3) type(Audio)
2009-05-04 15:28:54.541 VideoOutputXv: ProcessFrameXvMC: Tried to reuse frame but failed
2009-05-04 15:28:54.542 VideoOutputXv: ProcessFrameXvMC: Called without frame
2009-05-04 15:28:54.549 Opening audio device '/dev/dsp'. ch 2(2) sr 48000
2009-05-04 15:28:54.549 Opening OSS audio device '/dev/dsp'.
2009-05-04 15:28:54.560 NVP: Enabling Audio
2009-05-04 15:28:54.607 XvMC: picture structure FRAME
2009-05-04 15:28:54.695 NVP: prebuffering pause
2009-05-04 15:28:54.708 NVP: prebuffering pause
2009-05-04 15:28:54.722 NVP: prebuffering pause
2009-05-04 15:28:54.738 NVP: prebuffering pause
... and many more pauses until it crashes 

My /etc/X11/XvMCConfig has the following:
libXvMCNVIDIA_dynamic.so.1

Attached is my xorg.conf.   I wouldn't be surprised if something isn't quite right there.  I don't have a Dell 1905FP, but I'm not sure if I should get rid of that section.   I output to a SD TV at 640x480.   I was hoping the upgrade to Jaunty would fix the problem, but no luck.    Any help would be MUCH appreciated.
Thanks!
-Chris

---

### Post by ctcarroll on 2009-05-10
Recreated Xorg.conf, then reposted this issue under a new thread.  Please see [http://ubuntuforums.org/showthread.php?p=7253089#post7253089](http://ubuntuforums.org/showthread.php?p=7253089#post7253089)

---

