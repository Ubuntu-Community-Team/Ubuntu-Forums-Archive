---
title: "MythTV logs out user on &quot;Watch TV&quot;"
date: 2007-10-13
forum: Multimedia &amp; Video
---

### Post by ryth on 2007-10-13
Hi folks,

Total newb here with Mythtv, but I've been mucking around for hours and haven't been able to figure this out.

First my specs:
Feisty Amd-64
Compiz-Fusion
ATi X1950 (proprietary drivers)
Hauppauge PV-150

Problem:

1.  **When I load the MythTV front end, everything seems to be going okay until I click "Watch TV" at which point my machine logs out the user and I'm sitting at the login prompt.**    If i log in using regular Gnome without Compiz, I don't run into this problem, which leads me to believe there is some sort of compatibility issue or switch that I'm unaware with compiz?

2.  When I try to bring up the Channel listing/preview page (fi i get it running in plain Gnome), it shows on the screen for a monent, but before the preview and channel listings are loaded it crashes the front-end and dumps me to desktop.

Clearly issue #1 is the priority, but sorting both out would be nice.  Any suggestions are welcome, it's annoying to say the least that I get booted out like that.  Crashing to desktop is one thing, have to log in again every time when trying to troubleshoot is another.

I have included a part of my Mythtv log for reference, I am not sure really how to decipher it but figured it might be helpful.

> 2007-10-13 18:33:16.588 MainServer::HandleAnnounce Monitor
2007-10-13 18:33:16.592 adding: Compy as a client (events: 0)
2007-10-13 18:33:16.593 MainServer::HandleAnnounce Monitor
2007-10-13 18:33:16.594 adding: Compy as a client (events: 1)
2007-10-13 18:34:05.441 Expiring Unknown from Sat Oct 13 16:50:02 2007, 2 MBytes
, forced expire (LiveTV recording)
2007-10-13 18:35:47.017 MainServer::HandleAnnounce Monitor
2007-10-13 18:35:47.023 adding: Compy as a client (events: 0)
2007-10-13 18:35:47.024 MainServer::HandleAnnounce Monitor
2007-10-13 18:35:47.025 adding: Compy as a client (events: 1)
2007-10-13 18:35:47.027 MainServer::HandleAnnounce Playback
2007-10-13 18:35:47.028 adding: Compy as a client (events: 0)
2007-10-13 18:35:47.030 TVRec(1): Changing from None to WatchingLiveTV
2007-10-13 18:35:47.036 TVRec(1): HW Tuner: 1->1
2007-10-13 18:35:48.459 TVRec(1): Changing from WatchingLiveTV to None
2007-10-13 18:35:48.493 Finished recording Unknown: channel 1067


Thanks.

R

---

### Post by ryth on 2007-10-18
/gratuitous bump

---

### Post by cairn on 2007-10-20
I've got this exact same problem after upgrading to Gutsy this morning. MythTV worked fine under Feisty but since upgrading I get immediately logged out when attempting to watch live TV. Disabling Compiz does not seem to help.

I'm running Gutsy (upgraded from Feisty) on my AMD Athlon 64 X2 with a WinTV PVR 350 and using proprietary Nvidia drivers.

I don't know where to find the MythTV logs but I can provide them if someone can tell me where they're found. Any help is appreciated.

---

### Post by LazyRunner on 2007-10-22
I am having a similar issue.  I finally got my Mythbuntu using Gutsy up and running last night, but have not yet been able to see any TV.  Whenever I click "Watch TV" I see the schedule for about 2 seconds, then the entire Front End is gone (crashed).  I've found the logs at /var/log/mythtv/mythbackend.log and it gives me a message that says 
> 
2007-10-22 17:56:40.360 TVRec(4): Changing from None to WatchingLiveTV
2007-10-22 17:56:40.365 TVRec(4): HW Tuner: 4->4
strange error flushing buffer ... 
2007-10-22 17:56:44.428 TVRec(4): Changing from WatchingLiveTV to None
2007-10-22 17:56:44.735 Finished recording Unknown: channel 1000


Anyone know if there are any settings I'm supposed to change or update?

I am currently using a ATI TV Wonder VE to capture video, though I bought the Pinnacle PCTV HD PCI card from Woot a few weeks ago and I would much rather get that working.  If anyone knows what direction they can point me in finding possible drivers for that card, I'd be very appreciative.

---

### Post by cairn on 2007-10-22
Thanks LazyRunner for pointing out where to find the logs. Here's the output of my mythbackend.log:
```
2007-10-22 17:55:13.764 MainServer::HandleAnnounce Monitor
2007-10-22 17:55:13.770 adding: *[MyUserName]* as a client (events: 0)
2007-10-22 17:55:13.782 MainServer::HandleAnnounce Monitor
2007-10-22 17:55:13.782 adding:  *[MyUserName]* as a client (events: 1)
2007-10-22 17:55:13.783 Reschedule requested for id -1.
2007-10-22 17:55:13.821 Scheduled 0 items in 0.0 = 0.01 match + 0.02 place
2007-10-22 18:26:07.383 MainServer::HandleAnnounce Monitor
2007-10-22 18:26:07.385 adding:  *[MyUserName]* as a client (events: 0)
2007-10-22 18:26:07.386 MainServer::HandleAnnounce Monitor
2007-10-22 18:26:07.386 adding: *[MyUserName]* as a client (events: 1)
2007-10-22 18:26:07.440 MainServer::HandleAnnounce Playback
2007-10-22 18:26:07.454 adding:  *[MyUserName]* as a client (events: 0)
2007-10-22 18:26:07.475 TVRec(2): Changing from None to WatchingLiveTV
2007-10-22 18:26:07.478 TVRec(2): HW Tuner: 2->2
2007-10-22 18:26:09.829 TVRec(2): Changing from WatchingLiveTV to None
2007-10-22 18:26:10.228 Finished recording Unknown: channel 1042
```

and here's the output of my mythfrontend.log:
```
Starting mythfrontend.real..
2007-10-22 18:26:01.563 Current Schema Version: 1160
2007-10-22 18:26:01.564 mythfrontend version: 0.20.20070821-1 www.mythtv.org
2007-10-22 18:26:01.564 Enabled verbose msgs:  important general
2007-10-22 18:26:02.209 Total desktop dim: 1680x1050, with 1 screen[s].
2007-10-22 18:26:02.210 Running in a window
2007-10-22 18:26:02.210 Using screen 0, 1680x1000 at 0,25
2007-10-22 18:26:02.211 Switching to square mode (blue)
2007-10-22 18:26:02.308 Using the OpenGL painter
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2007-10-22 18:26:02.788 Joystick disabled.
2007-10-22 18:26:03.384 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-10-22 18:26:04.045 Registering Internal as a media playback plugin.
2007-10-22 18:26:04.761 Using NV NPOT texture extension
2007-10-22 18:26:07.340 New DB connection, total: 2
2007-10-22 18:26:07.340 Connected to database 'mythconverg' at host: localhost
2007-10-22 18:26:07.382 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2007-10-22 18:26:07.383 Using protocol version 31
2007-10-22 18:26:07.440 TV: Attempting to change from None to WatchingLiveTV
2007-10-22 18:26:07.440 Using protocol version 31
2007-10-22 18:26:09.018 AFD: Opened codec 0x8df4b50, id(MPEG2VIDEO) type(Video)
2007-10-22 18:26:09.045 AFD: Opened codec 0x8df51d0, id(MP2) type(Audio)
2007-10-22 18:26:09.096 Opening ALSA audio device 'default'.
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix.device'
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default
2007-10-22 18:26:09.102 AudioOutput Error: snd_pcm_open(default): No such file or directory
2007-10-22 18:26:09.102 NVP: Disabling Audio, reason is: snd_pcm_open(default): No such file or directory
2007-10-22 18:26:09.136 VideoOutputXv: XvMCTex: Init failed
2007-10-22 18:26:09.158 VideoOutputXv: XVideo Adaptor Name: 'Xgl Generic Texture Video'
mythfrontend.real: Fatal IO error: client killed
```

I don't know if this is relevant, but since encountering this problem with mythTV, I've tried using mplayer to watch TV but I can't seem to change channels using ivtv-tune either. Any help is appreciated!

---

### Post by cairn on 2007-10-22
Things are a lot easier to troubleshoot with log files! Since MythTV crashed immediately after attempting "VideoOutputXv", I tried disabling the nvidia "restricted drivers" and now I can watch TV in MythTV just fine!

This is still a problem for me since aparently MythTV doesn't work with the nvidia drivers in Gutsy and this is my main desktop machine so I need to use the nvidia drivers. The nvidia drivers worked with MythTV just fine in Feisty.

For now I'm going to continue to troubleshoot why I can't change channels using ivtv-tune and then try to watch TV in mplayer, but if I can help figure out why MythTV and the new nvidia drivers in gutsy don't work well together, let me know!

---

### Post by Zyith on 2007-10-23
I, too, have the same problem.  And like Cairn, turning off the restricted drivers fixes it.

I can't see why this should be the case -- with a hardware tuner, why should mythtv need more use of the graphics card than Gxine playing the files? 

This is really irritating, and has certainly helped cement my dislike of nvidia... it seems like every real problem I've had is caused by their stupid drivers.

---

### Post by JohnPhys on 2007-11-06
Any progress on this?  I'm running into it on a gutsy upgrade (nvidia card, watching tv on a frontend causes the frontend to log out)

--John

---

### Post by ryth on 2007-11-18
The only thing that I ended up finding that worked was disabling XGL, and then I would be able to watch tv.  I just installed the new distribution (clean) in hopes that it would correct the problem, but unfortunately no change.

The issue I am running in to now is there isn't an easy way (that i've found) in Gutsy to switch my session to non-xgl from the login.

Zyith:  This is happening to me with an ATI X1950, so it doesn't seem to be confined to the realms of Nvidia, for better or worse.

Anyone else come up with any novel solutions?

Also here is how far I got over on the Myth forums:

[http://www.mythtvtalk.com/forum/viewtopic.php?t=6624&highlight=](http://www.mythtvtalk.com/forum/viewtopic.php?t=6624&highlight=)

---

### Post by kooldino on 2007-11-19
I too, have this issue.  The only way I can actually watch TV is to log out and log back in in a Failsafe session.

Seems that Xgl still has it's issues.

I encountered the same problem with a game called Stepmania.  It doesn't play nice with Xgl.

Just curious - does anyone know of an easy way to temporarily disable xgl yet still log into my normal KDE desktop?

---

### Post by JohnPhys on 2007-11-20
I can't remember if this is related or not, but if you have the 'xserver-xgl' package installed, you might want to consider removing it.  I had it installed from when I tried compiz/xgl when I was on dapper, and completely forgot about it.  I removed xserver-xgl and it fixed some problems I was having with the nvidia drivers.  

I am still able to run with the restricted driver, with the compiz fusion options turned on, and MythTV won't log me out any more (sometimes the video from recordings doesn't show up correctly, but I think that's an unrelated issue).

NOTE:  In my case, when I removed xserver-xgl, it didn't want to remove any other packages (nothing seemed to depend on xserver-xgl).  If this is not the case for you, you should investigate further.

Another task I did was to enter synaptic and make sure the most recent gutsy version of myth was installed, as previous upgrades (dapper-> edgy, etc.) had left the old myth packages installed (probably since I was using backports).

Sorry that I can't be sure which one of those fixed the issue for me, I wish I would have taken better notes.

---

### Post by kooldino on 2007-11-20
You're running compiz without xserver-xgl installed?  How is that possible?

---

### Post by d0lph1nK1ng on 2007-11-21
same problem.

specs:
nvidia 7600
hauppauge pvr 150
32 bit P4
compiz fusion
dual screen (treated as 1 giant screen, not 1 screen extended onto another)

error log for frontend:
2007-11-20 23:01:07.873 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2007-11-20 23:01:07.894 Using protocol version 31
2007-11-20 23:01:07.913 TV: Attempting to change from None to WatchingLiveTV
2007-11-20 23:01:07.914 Using protocol version 31
2007-11-20 23:01:08.470 NVP: Disabling Audio, params(-1,2,44100)
2007-11-20 23:01:08.500 VideoOutputXv: XvMCTex: Init failed
2007-11-20 23:01:08.501 VideoOutputXv: XVideo Adaptor Name: 'Xgl Generic Texture Video'
mythfrontend.real: Fatal IO error: client killed

---

### Post by JohnPhys on 2007-11-27
Not sure, just know that I am.  I'm on my laptop at work now (non-nvidia, running fiesty), but I'll check my desktop when I get home to be sure.

Just as a side note, running dpkg -l | grep xgl in feisty turns up nothing, and I have the "desktop effects" stuff enabled for the cube effects and such, so xserver-xgl doesn't seem to be a requirement, unless I'm misunderstanding something.

---

### Post by ryth on 2007-12-01
> **kooldino said:**
> 
Just curious - does anyone know of an easy way to temporarily disable xgl yet still log into my normal KDE desktop?


See this thread here:

[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=616536](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=616536)

---

### Post by ryth on 2007-12-01
> **JohnPhys said:**
> Not sure, just know that I am.  I'm on my laptop at work now (non-nvidia, running fiesty), but I'll check my desktop when I get home to be sure.

Just as a side note, running dpkg -l | grep xgl in feisty turns up nothing, and I have the "desktop effects" stuff enabled for the cube effects and such, so xserver-xgl doesn't seem to be a requirement, unless I'm misunderstanding something.

If you are running nvidia you do not need to use xgl to run compiz, also if you are using the new ATI  driver you can bypass it as well.  If you are using ATI however I wouldn't suggest using the new driver (yet).  I tested it out and found my performance took a HUGE hit so went back to using xgl until things improve.

---

### Post by kubug on 2007-12-04
> **JohnPhys said:**
> I can't remember if this is related or not, but if you have the 'xserver-xgl' package installed, you might want to consider removing it.  I had it installed from when I tried compiz/xgl when I was on dapper, and completely forgot about it.  I removed xserver-xgl and it fixed some problems I was having with the nvidia drivers.  

I am still able to run with the restricted driver, with the compiz fusion options turned on, and MythTV won't log me out any more (sometimes the video from recordings doesn't show up correctly, but I think that's an unrelated issue).

NOTE:  In my case, when I removed xserver-xgl, it didn't want to remove any other packages (nothing seemed to depend on xserver-xgl).  If this is not the case for you, you should investigate further.



That did it for me. I had the same X server crashes in Gutsy with the restricted drivers and MythTV. 
After I ran 

sudo apt-get remove xserver-xgl 

everything works great now. Oh BTW, I do have compiz-fusion running as well.

---

### Post by ryth on 2007-12-05
> **kubug said:**
> That did it for me. I had the same X server crashes in Gutsy with the restricted drivers and MythTV. 
After I ran 

sudo apt-get remove xserver-xgl 

everything works great now. Oh BTW, I do have compiz-fusion running as well.

Can anyone confirm if this fix works with a ATI card, or if it is just an nvidia fix (as they dont have to use xgl?).

Thanks.

---

### Post by kooldino on 2007-12-05
> **ryth said:**
> If you are running nvidia you do not need to use xgl to run compiz, also if you are using the new ATI  driver you can bypass it as well.  If you are using ATI however I wouldn't suggest using the new driver (yet).  I tested it out and found my performance took a HUGE hit so went back to using xgl until things improve.

ORLY?

I'm running nvidia on one of my home boxes.  I got tired of the conflicts, so I uninstalled xserver-xgl, but now when I run compiz, I get no window manager.

This is on a Kubuntu 7.10 box that was upgraded from Kubuntu 7.04

---

### Post by ryth on 2007-12-05
> **kooldino said:**
> ORLY?

I'm running nvidia on one of my home boxes.  I got tired of the conflicts, so I uninstalled xserver-xgl, but now when I run compiz, I get no window manager.

This is on a Kubuntu 7.10 box that was upgraded from Kubuntu 7.04

I could be mistaken but that was my impression, however I'm an obvious newb.

I do believe you need to add "compiz --replace" into your  "sessions" regardless, so you may want to try that. (Although I have no experience with KDE)

(system -> preferences -> sessions).

---

### Post by kooldino on 2007-12-05
Not sure what the KDE equivalent of that is.

---

### Post by Tteddo on 2007-12-05
> **kubug said:**
> That did it for me. I had the same X server crashes in Gutsy with the restricted drivers and MythTV. 
After I ran 

sudo apt-get remove xserver-xgl 

everything works great now. Oh BTW, I do have compiz-fusion running as well.

I just did this on one of my laptops with Gutsy, Gnome, and Compiz and Compiz went away. MythTV works now, altho it's a little jerky.
It's a Acer 5050 dual core AMD w/ATI Radeon Express 1100 running with the restricted drivers. I run the MythTV Frontend with the backend on my living room computer.

---

### Post by Tteddo on 2007-12-05
This is odd, on this desktop I don't have xserver-xgl installed, yet Compiz is working great, with all the wobbly windows, etc...yet it killed all that on the laptop when I removed it.

---

### Post by ryth on 2007-12-05
> **Tteddo said:**
> This is odd, on this desktop I don't have xserver-xgl installed, yet Compiz is working great, with all the wobbly windows, etc...yet it killed all that on the laptop when I removed it.

Are you running Gutsy on both machines?  

Do both machines have ATI cards?

Remember  AFAIK - You only need XGL if you are using an ATI card and are **not** using the new ATI drivers.  

Perhaps your desktop is NVIDIA and your laptop is ATI?  Alternately if you have an ATI card on both you may have the new ATI driver installed on the desktop but not on the laptop?

---

### Post by kooldino on 2007-12-05
Can't wait to hear more on this...

---

### Post by Tteddo on 2007-12-05
> **ryth said:**
> Are you running Gutsy on both machines?  

Do both machines have ATI cards?

Remember  AFAIK - You only need XGL if you are using an ATI card and are **not** using the new ATI drivers.  

Perhaps your desktop is NVIDIA and your laptop is ATI?  Alternately if you have an ATI card on both you may have the new ATI driver installed on the desktop but not on the laptop?

Ahh...Desktop is nVidia 7300GS and the laptop is ATI (albeit with the newest restricted drivers). That explains it.

So...we know that removing xserver-xgl will fix the MythTV problem, anyone have any idea on a workaround or a fix?
I can't believe I miss the silly graphics. Up until a month ago my desktop was Win2000 with all the effects disabled, now I want my wobbly windows and rotating cube!!

---

### Post by kubug on 2007-12-09
I run the the latest nvidia BETA drivers for my 8600GT. Once I uninstalled the xgl-server Myth worked.

As far as the 3D desktop breaking, maybe it has to do with the fact that I run compiz-fusion and not compiz. Does compiz make use of the XGL server, while compiz-fusion doesn't.

BTW, mine is a fresh Gutsy install.

---

