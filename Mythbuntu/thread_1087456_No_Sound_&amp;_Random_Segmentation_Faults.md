---
title: "No Sound &amp; Random Segmentation Faults"
date: 2009-03-05
forum: Mythbuntu
---

### Post by Jonchilds on 2009-03-05
Hi All, 

I'm again having issues with getting my MythTV setup running properly.

I'm at the stage where I can get choppy/blocky video and no sound and have been ending up with Segmentation Fault errors (though not reproducible).

I've tried all the sound settings in Myth and get sound playback using me-tv on the standard speaker port.

Any comments/tips on getting this going nicely would be much appreciated.  Linux isn't my forte` but I'm learning to get around.

Latest copy from the frontend logs:
```
Starting mythfrontend.real..
2009-03-05 15:50:03.497 New DB connection, total: 2
2009-03-05 15:50:03.497 Connected to database 'mythconverg' at host: localhost
2009-03-05 15:50:03.498 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-03-05 15:50:03.498 Enabled verbose msgs:  important general
2009-03-05 15:50:03.678 Primary screen 0.
2009-03-05 15:50:03.678 Using screen 0, 1280x1024 at 0,0
2009-03-05 15:50:03.679 Switching to square mode (G.A.N.T)
2009-03-05 15:50:03.774 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2009-03-05 15:50:03.774 lirc_init failed for mythtv, see preceding messages
2009-03-05 15:50:03.775 JoystickMenuClient Error: Joystick disabled - Failed to read /home/jon/.mythtv/joystickmenurc
2009-03-05 15:50:05.354 Loading from: /usr/share/mythtv/themes/G.A.N.T/base.xml
2009-03-05 15:50:05.426 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-03-05 15:50:05.457 Registering Internal as a media playback plugin.
2009-03-05 15:51:15.113 Connecting to backend server: localhost:6543 (try 1 of 5)
2009-03-05 15:51:15.114 Using protocol version 40
2009-03-05 15:51:15.125 Received a remote 'Clear Cache' request
2009-03-05 15:51:19.163 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/status-ui.xml
2009-03-05 15:51:22.169 TV: Attempting to change from None to WatchingLiveTV
2009-03-05 15:51:22.170 Using protocol version 40
2009-03-05 15:51:23.259 NVP: Disabling Audio, params(-1,2,44100)
2009-03-05 15:51:23.314 VideoOutputXv Error: Could not find suitable XVideo surface.
2009-03-05 15:51:23.314 VideoOutputXv: Falling back to X11 video output over a network socket.
			      *** May be very slow ***
2009-03-05 15:51:23.314 VideoOutputXv Error: XCreateImage failed: XJ_disp(0xef6cd0) visual(0xa17f10) 
                        XJ_depth(24) WxH(1280x1024) bpl(3840)
2009-03-05 15:51:23.314 VideoOutputXv Error: Failed to create X buffers.
2009-03-05 15:51:23.442 Couldn't load deinterlace filter 
2009-03-05 15:51:23.445 OSD Theme Dimensions W: 640 H: 480
2009-03-05 15:51:23.880 TV: Changing from None to WatchingLiveTV
2009-03-05 15:51:23.882 Realtime priority would require SUID as root.
2009-03-05 15:51:23.892 Video timing method: USleep with busy wait
2009-03-05 15:51:26.054 AFD: codec MP3 has 2 channels
2009-03-05 15:51:26.054 AFD: Opened codec 0x7f4518054310, id(MP3) type(Audio)
2009-03-05 15:51:26.060 VideoOutputXv Error: Could not find suitable XVideo surface.
2009-03-05 15:51:26.060 VideoOutputXv: Falling back to X11 video output over a network socket.
			      *** May be very slow ***
2009-03-05 15:51:26.060 VideoOutputXv Error: XCreateImage failed: XJ_disp(0xef6cd0) visual(0xa17f10) 
                        XJ_depth(24) WxH(1280x1024) bpl(3840)
2009-03-05 15:51:26.060 VideoOutputXv Error: Failed to create X buffers.
2009-03-05 15:51:26.352 AFD: Opened codec 0x7f45180673d0, id(MPEG2VIDEO) type(Video)
2009-03-05 15:51:26.477 Opening audio device 'analog'. ch 2(2) sr 48000
2009-03-05 15:51:26.477 Opening ALSA audio device 'analog'.
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM analog
2009-03-05 15:51:26.479 AudioOutput Error: snd_pcm_open(analog): No such file or directory
2009-03-05 15:51:26.479 NVP: Disabling Audio, reason is: snd_pcm_open(analog): No such file or directory
2009-03-05 15:51:27.431 [mpeg2video @ 0x7f45313555b0]Warning MVs not available
2009-03-05 15:51:29.390 [mpeg2video @ 0x7f45313555b0]ac-tex damaged at 40 31
2009-03-05 15:51:29.390 [mpeg2video @ 0x7f45313555b0]Warning MVs not available
2009-03-05 15:51:30.468 [mpeg2video @ 0x7f45313555b0]ac-tex damaged at 8 8
2009-03-05 15:51:30.470 [mpeg2video @ 0x7f45313555b0]Warning MVs not available
2009-03-05 15:51:31.508 [mpeg2video @ 0x7f45313555b0]ac-tex damaged at 38 7
2009-03-05 15:51:31.508 [mpeg2video @ 0x7f45313555b0]ac-tex damaged at 41 11
2009-03-05 15:51:34.187 NVP: prebuffering pause
2009-03-05 15:51:34.528 New DB connection, total: 3
2009-03-05 15:51:34.529 Connected to database 'mythconverg' at host: localhost
2009-03-05 15:51:37.442 VideoOutputXv Error: Could not find suitable XVideo surface.
2009-03-05 15:51:37.442 VideoOutputXv: Falling back to X11 video output over a network socket.
			      *** May be very slow ***
2009-03-05 15:51:37.442 VideoOutputXv Error: XCreateImage failed: XJ_disp(0xef6cd0) visual(0xa17f10) 
                        XJ_depth(24) WxH(1280x1024) bpl(3840)
2009-03-05 15:51:37.443 VideoOutputXv Error: Failed to create X buffers.
2009-03-05 15:51:37.761 NVP: Prebuffer wait timed out 10 times.
2009-03-05 15:51:37.937 AFD: Opened codec 0x7f451a494120, id(MPEG2VIDEO) type(Video)
2009-03-05 15:51:37.937 AFD: codec AC3 has 6 channels
2009-03-05 15:51:37.937 AFD: Opened codec 0x7f451a4f5520, id(AC3) type(Audio)
2009-03-05 15:51:37.983 Opening audio device 'analog'. ch 2(2) sr 48000
2009-03-05 15:51:37.983 Opening ALSA audio device 'analog'.
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM analog
2009-03-05 15:51:37.983 AudioOutput Error: snd_pcm_open(analog): No such file or directory
2009-03-05 15:51:37.983 NVP: Disabling Audio, reason is: snd_pcm_open(analog): No such file or directory
2009-03-05 15:51:38.262 [mpeg2video @ 0x7f45313555b0]ac-tex damaged at 104 64
2009-03-05 15:51:38.262 [mpeg2video @ 0x7f45313555b0]invalid mb type in I Frame at 102 67
2009-03-05 15:51:38.262 [mpeg2video @ 0x7f45313555b0]invalid mb type in I Frame at 80 1
2009-03-05 15:51:38.262 [mpeg2video @ 0x7f45313555b0]invalid mb type in I Frame at 0 2
2009-03-05 15:51:38.262 [mpeg2video @ 0x7f45313555b0]invalid mb type in I Frame at 40 2
2009-03-05 15:51:38.262 [mpeg2video @ 0x7f45313555b0]invalid mb type in I Frame at 80 2
2009-03-05 15:51:38.262 [mpeg2video @ 0x7f45313555b0]invalid mb type in I Frame at 0 3
2009-03-05 15:51:38.262 [mpeg2video @ 0x7f45313555b0]invalid mb type in I Frame at 40 3
2009-03-05 15:51:38.262 [mpeg2video @ 0x7f45313555b0]invalid mb type in I Frame at 80 4
2009-03-05 15:51:38.262 [mpeg2video @ 0x7f45313555b0]invalid mb type in I Frame at 0 7
2009-03-05 15:51:38.262 [mpeg2video @ 0x7f45313555b0]invalid mb type in I Frame at 40 7
2009-03-05 15:51:38.262 [mpeg2video @ 0x7f45313555b0]invalid mb type in I Frame at 80 7
2009-03-05 15:51:38.262 [mpeg2video @ 0x7f45313555b0]invalid mb type in I Frame at 0 8
2009-03-05 15:51:38.262 [mpeg2video @ 0x7f45313555b0]ac-tex damaged at 40 
...cut repeated comments as above...
2009-03-05 15:52:06.219 [mpeg2video @ 0x7f45313555b0]ac-tex damaged at 62 34
2009-03-05 15:52:07.338 TV: Attempting to change from WatchingLiveTV to None
2009-03-05 15:52:07.751 TV: Changing from WatchingLiveTV to None
```

---

