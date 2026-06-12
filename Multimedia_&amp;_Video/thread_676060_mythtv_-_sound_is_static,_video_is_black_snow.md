---
title: "mythtv - sound is static, video is black snow"
date: 2008-01-23
forum: Multimedia &amp; Video
---

### Post by aBitLater on 2008-01-23
Hello,

I'm having a bit of trouble with mythtv.  everything appears to work except "watch tv".  I've watched live video streams and listened to a "beer cast" successfully.  But the tv gives only black screen with a little snow, and static sound.

One thing I'm wondering is if I have to use the proprietary driver for my ATI Radeon 9700 Pro? 

fglrxinfo reveals this (if it matters):
```
display: :0.0  screen: 0
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 AGP 4x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.1

```

Also, if there is a conflict only with the sound setup, will that affect the video too? I.e, if I fix one problem, maybe I'll fix the other also.

My tuner is Hauppauge WinTV PVR 150 (PCI card) with analog US  cable.  I've successfully recorded tv with ivtv - but being the noob that I am, I don't know if that matters or not :)  I'm using Gutsy 7.10 (and loving it, btw).

Any help is greatly appreciated!  TIA for your time!

I'll be happy to post any other logs or information if you can tell me how or where to retrieve it.

Here is a piece of the mythfrontend.log that I thought looked as though it might apply:

```

2008-01-23 11:18:29.565 TV: Attempting to change from None to WatchingLiveTV
2008-01-23 11:18:29.565 Using protocol version 31
2008-01-23 11:18:30.847 AFD: Opened codec 0x82c4e90, id(MPEG2VIDEO) type(Video)
2008-01-23 11:18:30.865 AFD: Opened codec 0x82c78d0, id(MP2) type(Audio)
2008-01-23 11:18:30.960 Opening ALSA audio device 'default'.
2008-01-23 11:18:31.008 VideoOutputXv: XvMCTex: Init failed
2008-01-23 11:18:31.009 VideoOutputXv: XVideo Adaptor Name: 'ATI Radeon Video Overlay'
2008-01-23 11:18:31.394 TV: Changing from None to WatchingLiveTV
2008-01-23 11:18:31.402 Realtime priority would require SUID as root.
2008-01-23 11:18:31.406 New DB connection, total: 3
2008-01-23 11:18:31.406 Connected to database 'mythconverg' at host: localhost
2008-01-23 11:18:31.469 XMLParse::LoadTheme using /usr/share/mythtv/themes/G.A.N.T./ui.xml
2008-01-23 11:18:31.577 Video timing method: DRM
2008-01-23 11:18:33.674 NVP: prebuffering pause
2008-01-23 11:18:33.677 WriteAudio: buffer underrun
2008-01-23 11:18:46.169 XMLParse::LoadTheme using /usr/share/mythtv/themes/G.A.N.T./ui.xml
2008-01-23 11:19:13.313 XMLParse::LoadTheme using /usr/share/mythtv/themes/G.A.N.T./ui.xml
2008-01-23 11:19:17.148 NVP: prebuffering pause
2008-01-23 11:19:28.594 XMLParse::LoadTheme using /usr/share/mythtv/themes/G.A.N.T./ui.xml
2008-01-23 11:19:55.084 TV: Attempting to change from WatchingLiveTV to None
2008-01-23 11:19:55.340 TV: Changing from WatchingLiveTV to None

```

---

### Post by dannyboy79 on 2008-01-23
have you checked this out?

[https://help.ubuntu.com/community/MythTV_Edgy_hardware](https://help.ubuntu.com/community/MythTV_Edgy_hardware)

---

### Post by aBitLater on 2008-01-23
> 
have you checked this out?

[https://help.ubuntu.com/community/MythTV_Edgy_hardware](https://help.ubuntu.com/community/MythTV_Edgy_hardware)


Thanks for the input.  However, I don't have a problem installing the ATI Proprietary driver in Gutsy... I've had issues with it though.  1600x1200 resolution causes flicker on the screen.  And (with any resolution) glxgears makes my display blank on and off with the proprietary driver - so I assume the mesa driver is better for me (?)

The tuner info at that page was a little sparse.  I have checked out several how-to pages and trouble-shooting docs - none that I've seen address the issue posted

Thanks again.

---

### Post by dannyboy79 on 2008-01-23
well 2 items in the log look out of place:

VideoOutputXv: XvMCTex: Init failed

and

Realtime priority would require SUID as root.

the first error is why I pointed out using a different video card driver. have you tried to start the frontend with logging or debugging info enabled so that it outputs the log or debug info to a file? you would do that by issuing this at the command line

mythfrontend 2>&1 >> frontend.log

then you could view frontend.log to see what it says.

---

### Post by aBitLater on 2008-01-23
DannyBoy

i installed the proprietary driver through Ubuntu's Restricted Driver applet, and ran the command you mentioned from a 'root' terminal

after doing that, but before mythtvfrontend became active, this error was in the terminal:
```
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
```

The first part is no big deal, AFAIK, but I don't know about the socket stuff.  I'm not worried about the infra-red remote control error, as I don't have one.

Here's the frontend.log from that session. I've highlighted my best guesses on the lines that cause problems...

Again, thank you for your time!

```
2008-01-23 12:55:37.419 Using runtime prefix = /usr
2008-01-23 12:55:37.435 DPMS is active.
2008-01-23 12:55:37.477 New DB connection, total: 1
2008-01-23 12:55:37.481 Connected to database 'mythconverg' at host: localhost
2008-01-23 12:55:37.482 Total desktop dim: 1280x1024, with 1 screen[s].
2008-01-23 12:55:37.485 Using screen 0, 1280x1024 at 0,0
2008-01-23 12:55:37.494 Current Schema Version: 1160
2008-01-23 12:55:37.496 mythfrontend version: 0.20.20070821-1 www.mythtv.org
2008-01-23 12:55:37.496 Enabled verbose msgs:  important general
2008-01-23 12:55:38.391 Total desktop dim: 1280x1024, with 1 screen[s].
2008-01-23 12:55:38.393 Using screen 0, 1280x1024 at 0,0
2008-01-23 12:55:38.394 Switching to square mode (G.A.N.T.)
2008-01-23 12:55:38.496 Using the Qt painter
2008-01-23 12:55:38.813 Joystick disabled.
2008-01-23 12:56:08.351 Loading from: /usr/share/mythtv/themes/G.A.N.T./base.xml
2008-01-23 12:56:08.373 Loading from: /usr/share/mythtv/themes/default/base.xml
**2008-01-23 12:56:08.503 Registering Internal as a media playback plugin.**
2008-01-23 12:56:08.660 Registering MythDVD DVD Media Handler as a media handler ext()
2008-01-23 12:56:08.661 Registering MythDVD VCD Media Handler as a media handler ext()
SIP listening on IP Address 192.168.1.91:5060 NAT address 192.168.1.91
SIP: Cannot register; proxy, username or password not set
2008-01-23 12:56:12.271 New DB connection, total: 2
2008-01-23 12:56:12.271 Connected to database 'mythconverg' at host: localhost
2008-01-23 12:56:12.309 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-01-23 12:56:12.334 Using protocol version 31
[b]2008-01-23 12:56:12.350 TV: Attempting to change from None to WatchingLiveTV
2008-01-23 12:56:12.350 Using protocol version 31
2008-01-23 12:56:14.195 DPMS Deactivated 
2008-01-23 12:56:14.381 AFD: Opened codec 0x82bdd70, id(MPEG2VIDEO) type(Video)
2008-01-23 12:56:14.420 AFD: Opened codec 0x82cc8d0, id(MP2) type(Audio)
2008-01-23 12:56:14.509 Opening ALSA audio device 'default'.
2008-01-23 12:56:14.557 VideoOutputXv: XvMCTex: Init failed
2008-01-23 12:56:14.590 VideoOutputXv Error: Could not find suitable XVideo surface.
2008-01-23 12:56:14.590 VideoOutputXv: Falling back to X shared memory video output.
			      *** May be slow ***[/b]
2008-01-23 12:56:15.187 TV: Changing from None to WatchingLiveTV
2008-01-23 12:56:15.190 New DB connection, total: 3
2008-01-23 12:56:15.191 Connected to database 'mythconverg' at host: localhost
2008-01-23 12:56:15.193 Using realtime priority.
2008-01-23 12:56:15.231 Video timing method: RTC
2008-01-23 12:56:15.269 XMLParse::LoadTheme using /usr/share/mythtv/themes/G.A.N.T./ui.xml
2008-01-23 12:56:19.067 NVP: prebuffering pause
2008-01-23 12:56:19.503 RingBuf(/var/lib/mythtv/recordings/1036_20080123125612.mpg): Waited 1.0 seconds for data to become available...
2008-01-23 12:56:19.504 Checking to see if there's a new livetv program to switch to..
2008-01-23 12:56:20.011 VideoOutputXv Error: 
***
* Your system is not capable of displaying the
* full framerate at 384x307 resolution.  Frames
* will be skipped in order to keep the audio and
* video in sync.

2008-01-23 12:56:32.634 TV: Attempting to change from WatchingLiveTV to None
2008-01-23 12:56:32.772 TV: Changing from WatchingLiveTV to None
2008-01-23 12:56:32.779 DPMS Reactivated.
Destroying SipFsm object 

```

---

### Post by dannyboy79 on 2008-01-23
have you checked XvMC in mythtv and use BOB interlacer? I am not really sure as I don't use ATI cards for video output. check out this thread and it may help:
[http://ubuntuforums.org/showthread.php?t=404863](http://ubuntuforums.org/showthread.php?t=404863)

---

### Post by aBitLater on 2008-01-23
Ok, I'll check out that link now... 

I wanted to post the mythbackend.log here as well :

Do you know anything about binding video sources to my card's inputs?  (see bold below)

```

2008-01-23 13:35:03.309 New DB connection, total: 2
2008-01-23 13:35:03.311 Connected to database 'mythconverg' at host: localhost
2008-01-23 13:35:03.314 EITHelper: localtime offset -5:00:00 
2008-01-23 13:35:03.320 New DB connection, total: 3
2008-01-23 13:35:03.322 Connected to database 'mythconverg' at host: localhost
2008-01-23 13:35:03.485 EITHelper: localtime offset -5:00:00 
[b]2008-01-23 13:35:03.488 TVRec(2) Error: Problem finding starting channel, setting to default of '3'.
2008-01-23 13:35:03.489 ChannelBase(2) Error: InitializeInputs(): 
			Could not get inputs for the capturecard.
			Perhaps you have forgotten to bind video
			sources to your card's inputs? [/b]
2008-01-23 13:35:03.492 New DB scheduler connection
2008-01-23 13:35:03.493 Connected to database 'mythconverg' at host: localhost
2008-01-23 13:35:07.122 Using runtime prefix = /usr
2008-01-23 13:35:07.175 New DB connection, total: 1
2008-01-23 13:35:07.184 Connected to database 'mythconverg' at host: localhost
2008-01-23 13:35:07.188 Current Schema Version: 1160
Starting up as the master server.
2008-01-23 13:35:07.200 New DB connection, total: 2
2008-01-23 13:35:07.202 Connected to database 'mythconverg' at host: localhost
2008-01-23 13:35:07.205 EITHelper: localtime offset -5:00:00 
2008-01-23 13:35:07.210 New DB connection, total: 3
2008-01-23 13:35:07.213 Connected to database 'mythconverg' at host: localhost
2008-01-23 13:35:07.367 EITHelper: localtime offset -5:00:00 
2008-01-23 13:35:07.370 TVRec(2) Error: Problem finding starting channel, setting to default of '3'.
2008-01-23 13:35:07.371 ChannelBase(2) Error: InitializeInputs(): 
			Could not get inputs for the capturecard.
			Perhaps you have forgotten to bind video
			sources to your card's inputs?
2008-01-23 13:35:07.373 New DB scheduler connection
2008-01-23 13:35:07.374 Connected to database 'mythconverg' at host: localhost
2008-01-23 13:35:08.754 Main::Registering HttpStatus Extension
2008-01-23 13:35:08.758 mythbackend version: 0.20.20070821-1 www.mythtv.org
2008-01-23 13:35:08.759 Enabled verbose msgs:  important general
2008-01-23 13:35:08.760 AutoExpire: Found 1 recorders w/max rate of 72 MiB/min
2008-01-23 13:35:08.762 AutoExpire: Required Free Space: 2.1 GB w/freq: 10 min
2008-01-23 13:35:09.380 Reschedule requested for id -1.
2008-01-23 13:35:09.475 Scheduled 0 items in 0.1 = 0.08 match + 0.02 place
2008-01-23 13:35:09.480 Seem to be woken up by USER
2008-01-23 13:37:22.440 MainServer::HandleAnnounce Monitor
2008-01-23 13:37:22.445 adding: myubu as a client (events: 0)
2008-01-23 13:37:22.446 MainServer::HandleAnnounce Monitor
2008-01-23 13:37:22.447 adding: myubu as a client (events: 1)
2008-01-23 13:37:22.461 Reschedule requested for id 0.
2008-01-23 13:37:22.507 Scheduled 0 items in 0.0 = 0.00 match + 0.04 place
2008-01-23 13:37:51.200 Reschedule requested for id 0.
2008-01-23 13:37:51.250 Scheduled 0 items in 0.0 = 0.00 match + 0.05 place
2008-01-23 13:39:25.509 Reloading backend settings
2008-01-23 13:41:05.859 MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 2
2008-01-23 13:41:42.350 MainServer::HandleAnnounce Playback
2008-01-23 13:41:42.353 adding: myubu as a client (events: 0)
2008-01-23 13:41:42.355 TVRec(1): Changing from None to WatchingLiveTV
2008-01-23 13:41:42.361 TVRec(1): HW Tuner: 1->1
2008-01-23 13:42:01.886 TVRec(1): Changing from WatchingLiveTV to None
2008-01-23 13:42:01.969 Finished recording Power Lunch: channel 1036

```

---

### Post by aBitLater on 2008-01-23
ok, i made some progress using ivtv-tune to change the channel, while mythtvfrontend is running.

now I get sound, but no video (well, about 1/2 the video window has 3 frames of "squiggly" lines in it, the bottom 1/2 or 2/3 of screen is black)

---

### Post by dannyboy79 on 2008-01-23
well, within mythtv-setup, you should be chosing a video source, whether you use schedulesdirect or some other source.

---

### Post by aBitLater on 2008-01-23
I'm using schedulesdirect.

I feel like a doof - I hit "escape" on the frontend and the messed-up tiny window (with the channel listings) went away and I got a full-screen tv.

It's "working" now (not the preview window) in full screen, but the video looks like it's running just a bit in slow motion.

I'll keep following links and how-to's , but I get a little confused sometimes :)

---

### Post by aBitLater on 2008-01-23
Ok, I've got the resolution down to 640x480, much nicer

This error still appears in my log file 

```

2008-01-23 14:41:16.369 VideoOutputXv: XvMCTex: Init failed
2008-01-23 14:41:16.370 VideoOutputXv Error: Could not find suitable XVideo surface.
2008-01-23 14:41:16.370 VideoOutputXv: Falling back to X shared memory video output.
			      *** May be slow ***

```

What I've read so far on XvMC is a little beyond me.  When the tutorials start talking about kernel drivers, modules, compiling the kernel, etc, my palms get sweaty. :)

Will have to keep reading.

I'm using ivtv-tune in a terminal to change the channels... is there an easier way?  If I hit enter on the channel listing in the frontend, it just gives me options for recording.

---

### Post by dannyboy79 on 2008-01-23
within mythtv-setup, did you check the box to tell it to use xvmc? what driver are you using for your videocard?

---

### Post by aBitLater on 2008-01-23
where is the option for xvmc?

I enabled the proprietary driver for ATI Radeon 9700 Pro, but fglrxinfo reports

```

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

```

I'll try to get the proprietary driver working.

---

### Post by dannyboy79 on 2008-01-23
sorry, it's in the frontend settings somewhere not the mythtv-setup. here's a thread that may help if I didn't already post this:
[http://ubuntuforums.org/archive/index.php/t-404863.html](http://ubuntuforums.org/archive/index.php/t-404863.html)

---

