---
title: "[SOLVED] Is my hardware good enough?"
date: 2008-05-03
forum: Mythbuntu
---

### Post by tinny on 2008-05-03
Hi

Im wanting to get a Mythbuntu system up and running. I have a Technotrend S-1401 DVB-S Card that I am wanting to use to view satellite TV. 

I have installed this card into a HP pavilion 721a PC. I have done a Mythbuntu backend and frontend install on this computer. When I try to watch live TV it works for about 1sec and then freezes.

My PC's spec is as follows:

1.6 GHz Intel Pentium 4 Processor
757 MB RAM
Some type of ATI 256MB graphics card...

Im guessing that my system is under powered, right?

Are there any optimizations that I could make to get this to work?

Any help would be great!!! Thanks

---

### Post by volkswagner on 2008-05-03
You can check logs and post here.  /var/log/mythtv/mythfronten.log and /var/log/mythtv/mythbackend.log.

You may also need to change tv playback settings, use onpengl, or not depending if you video card supports it.  Change the deinterlacer, renderer, etc.  The system has prefab. settings.  You can toggle through cpu--, cpu+, cpu++, etc.  Do this before making any changes to settings to see if one works for you.

---

### Post by tinny on 2008-05-03
Hi, thanks for the reply.

I have attached my log files.

I tried all of the things that you suggested. Enabled opengl, tried cpu+, cpu++, cpu--, slim, High Quality and normal settings. Normal showed a frozen picture with no sound and all of the other settings showed a frozen picture with jumpy sound.

Any ideas? Thanks

---

### Post by kreegor on 2008-05-03
> **tinny said:**
> Hi

My PC's spec is as follows:

1.6 GHz Intel Pentium 4 Processor
757 MB RAM
Some type of ATI 256MB graphics card...

Im guessing that my system is under powered, right?

Are there any optimizations that I could make to get this to work?

Any help would be great!!! Thanks

Hey, I would suggest getting at least 1 gig of ram if you can. I found my machine was using up around 800 - 900 meg of ram when watching TV so yours would be chewing into the page file and slowing things down.

That's about all I can really suggest.

---

### Post by volkswagner on 2008-05-03
I am not running 8.04 so I may not be much help.  It seems you have sound related problems.  I get the audio buffer problems when trying to play multi channel audio with 2ch selected in general settings, frontend, page 3.  You may want to post the output of

```
aplay -l
```

and 

```
aplay -L
```

Again, I am not running 8.04, but I thought pulse audio was default.  I see you are calling alsa for sound.  You may need further config on alsa.

I also see the backend errors related to /var/lib/mythtv/recordings.  Check the permissions for this folder.  Also make sure you have enough hard disk space.  I see your max reserve went from 1gig to 3gig.  Did you make that change?

Can you schedule and watch a recording?

---

### Post by tinny on 2008-05-05
> **kreegor said:**
> Hey, I would suggest getting at least 1 gig of ram if you can. I found my machine was using up around 800 - 900 meg of ram when watching TV so yours would be chewing into the page file and slowing things down.

That's about all I can really suggest.

Thanks for the suggestion.

When I am recording (sort of recording!!!) my system is only using 35MB of swap, not good but also not too bad right?

---

### Post by tinny on 2008-05-05
I have stereo selected in the general settings.

Here is the output from those commands you suggested.

```

>aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```

>aplay -L
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
sean@mythbuntu:~$ aplay -L
default:CARD=SI7012
    SiS SI7012, SiS SI7012
    Default Audio Device
front:CARD=SI7012,DEV=0
    SiS SI7012, SiS SI7012
    Front speakers
surround40:CARD=SI7012,DEV=0
    SiS SI7012, SiS SI7012
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SI7012,DEV=0
    SiS SI7012, SiS SI7012
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SI7012,DEV=0
    SiS SI7012, SiS SI7012
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SI7012,DEV=0
    SiS SI7012, SiS SI7012
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
iec958:CARD=SI7012,DEV=0
    SiS SI7012, SiS SI7012
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=UART
    MPU-401 UART
    Default Audio Device

```

Also...

From the control centre I could see that mythbuntu was being run as the user "sean". So I changed the "sean" user to be the owner of the recordings folder.

Next...

I scheduled a recording and it seemed to work (only using 35MB of swap), however when I played the recording it was the same freeze frame that I got. Also I could see this recording in my recordings folder (so mythbuntu can write to that folder), it was 540MB for 10mins. I tried to play the recording using totem and could not (I have all my codecs installed).

I did not change the reserve to 3gig. I have well over 40gigs free on my HD.

More info...

I should also detail how I did my install. I first installed Ubuntu 8.04 desktop over the network using a mini ISO, I did this because my CD ROM drive is broken and I can only read a small amount of data. Then I installed Mythbuntu using the install Mythbuntu link on the web site.

Thanks for the help!!!

---

### Post by volkswagner on 2008-05-05
I am not sure if you have sound and video issues or what.  More questions, what are you using for a display device, and output from card?  Are you using the restricted drivers.  If you don't know your video card you can find it via  and post it here.

```
lspci
```

To sort out, can you play audio files?  Since your CDROM is broken can you add some mp3 files to your music folder?  Play the mp3 files via mythtv.  Before playing open a terminal and use the following to get your log in real time.

```
tail -f /var/log/mythtv/mythfrontend.log
```

Post back results.  

How is your sound connected?  I see you have default selected.  What is listed as default in
```

nano /home/sean/.asoundrc.asoundconf
```

Do you have a file for /home/sean/.asoundrc?

---

### Post by volkswagner on 2008-05-05
Tinny,

Try the following for tv playback settings.

Try with opengl enabled, select cpu++ and edit so if rez is > 0 0(so it will always use this, you can delete others withing this profile to make sure the system is using just these settings), libmpeg2 and XVideo, linearblend deinterlace, same for fallback, try several video renderer's (I have DirectX working).  Do the same with -tail /var/log....

---

### Post by tinny on 2008-05-06
> I am not sure if you have sound and video issues or what. More questions, what are you using for a display device, and output from card? Are you using the restricted drivers. If you don't know your video card you can find it via and post it here.

I have connected to my TV using the s-video port on my card. I am using the restricted ATI driver that the restricted drivers manager prompted me about after install (I cant use s-video without it).

Also...

```

>lspci

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS961 [MuTIOL Media IO]
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:0f.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)
```

Next I installed Mythvideo and Mythmusic. I then played a music track (mp3) and a video (mpg) and both played very well!!! The only problem was that the sound was quiet.

Here is the log from playing the above music and video files (in that order).

```

2008-05-06 18:38:57.032 VideoOutputXv Error: Failed to create X buffers.
2008-05-06 18:38:57.442 Couldn't load deinterlace filter
2008-05-06 18:38:57.520 OSD Theme Dimensions W: 640 H: 480
2008-05-06 18:38:58.635 TV: Changing from None to WatchingPreRecorded
2008-05-06 18:38:58.641 Realtime priority would require SUID as root.
2008-05-06 18:38:59.178 Video timing method: USleep with busy wait
2008-05-06 18:38:59.178 WriteAudio: buffer underrun
2008-05-06 18:39:20.626 TV: Attempting to change from WatchingPreRecorded to None
2008-05-06 18:39:20.711 TV: Changing from WatchingPreRecorded to None
2008-05-06 18:39:21.724 DPMS Reactivated.
Starting mythfrontend.real..
2008-05-06 18:40:42.080 New DB connection, total: 2
2008-05-06 18:40:42.081 Connected to database 'mythconverg' at host: localhost
2008-05-06 18:40:42.093 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-05-06 18:40:42.093 Enabled verbose msgs:  important general
2008-05-06 18:40:42.309 Unable to parse themeinfo.xml for glass-wide
2008-05-06 18:40:42.310 The theme (glass-wide) is missing a themeinfo.xml file
2008-05-06 18:40:42.649 Unable to parse themeinfo.xml for glass-wide
2008-05-06 18:40:42.649 The theme (glass-wide) is missing a themeinfo.xml file
2008-05-06 18:40:43.199 Primary screen 0.
2008-05-06 18:40:43.200 Using screen 0, 1280x1024 at 0,0
2008-05-06 18:40:43.203 Switching to square mode (G.A.N.T)
2008-05-06 18:40:43.464 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2008-05-06 18:40:43.465 lirc_init failed for mythtv, see preceding messages
2008-05-06 18:40:43.465 JoystickMenuClient Error: Joystick disabled - Failed to read /home/sean/.mythtv/joystickmenurc
2008-05-06 18:40:46.294 Loading from: /usr/share/mythtv/themes/G.A.N.T/base.xml
2008-05-06 18:40:46.495 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-05-06 18:40:46.775 Registering Internal as a media playback plugin.
2008-05-06 18:40:47.191 MythMusic adding CD-Writer: 1,0,0 -- CD-RW  CRX230E 
2008-05-06 18:40:47.476 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2008-05-06 18:40:57.262 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/video-ui.xml
2008-05-06 18:40:58.715 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/video-ui.xml
2008-05-06 18:41:00.290 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-05-06 18:41:00.293 Using protocol version 40
2008-05-06 18:41:00.308 TV: Attempting to change from None to WatchingPreRecorded
2008-05-06 18:41:00.336 DPMS Deactivated
2008-05-06 18:41:00.635 AFD: Opened codec 0x8ac73f0, id(MPEG2VIDEO) type(Video)
2008-05-06 18:41:00.635 AFD: codec MP2 has 2 channels
2008-05-06 18:41:00.635 AFD: Opened codec 0x8ac18c0, id(MP2) type(Audio)
2008-05-06 18:41:00.645 Opening audio device 'default'. ch 2(2) sr 44100
2008-05-06 18:41:00.646 Opening ALSA audio device 'default'.
2008-05-06 18:41:00.909 VideoOutputXv Error: Could not find suitable XVideo surface.
2008-05-06 18:41:00.909 VideoOutputXv: Falling back to X11 video output over a network socket.
                  *** May be very slow ***
2008-05-06 18:41:00.910 VideoOutputXv Error: XCreateImage failed: XJ_disp(0x8396f60) visual(0x838ed18)
                        XJ_depth(24) WxH(1280x1024) bpl(3840)
2008-05-06 18:41:00.910 VideoOutputXv Error: Failed to create X buffers.
2008-05-06 18:41:01.370 Couldn't load deinterlace filter
2008-05-06 18:41:01.384 OSD Theme Dimensions W: 640 H: 480
2008-05-06 18:41:02.058 TV: Changing from None to WatchingPreRecorded
2008-05-06 18:41:02.124 WriteAudio: buffer underrun
2008-05-06 18:41:02.127 Realtime priority would require SUID as root.
2008-05-06 18:41:02.203 Video timing method: USleep with busy wait
2008-05-06 18:41:05.673 TV: Attempting to change from WatchingPreRecorded to None
2008-05-06 18:41:05.797 TV: Changing from WatchingPreRecorded to None
2008-05-06 18:41:06.869 DPMS Reactivated.
2008-05-06 18:41:11.818 New DB connection, total: 3
2008-05-06 18:41:11.819 Connected to database 'mythconverg' at host: localhost
2008-05-06 18:41:11.889 XMLParse::LoadTheme using /usr/share/mythtv/themes/G.A.N.T/music-ui.xml
2008-05-06 18:41:13.129 Opening audio device 'default'. ch 2(2) sr 44100
2008-05-06 18:41:13.130 Opening ALSA audio device 'default'.

```

> 
Do you have a file for /home/sean/.asoundrc?


No I do not...?

---

### Post by tinny on 2008-05-06
> **volkswagner said:**
> Tinny,

Try the following for tv playback settings.

Try with opengl enabled, select cpu++ and edit so if rez is > 0 0(so it will always use this, you can delete others withing this profile to make sure the system is using just these settings), libmpeg2 and XVideo, linearblend deinterlace, same for fallback, try several video renderer's (I have DirectX working).  Do the same with -tail /var/log....

I edited cpu++ and tried many different combinations. Most where bad. 

But I did find a combination that "sort of" worked :-)

Decoder: libmpeg2
Video Renderer: xshm
OSD Renderer: softblend
Primary Deinterlacer: None
Fallback Deinterlcer: None

The sound was good but quiet.
The video was very jumpy but didnt freeze.

Here is the log output while using these settings (so a little bit of progress :-) )

```

2008-05-06 20:47:12.074 FilterManager: failed to load filter 'none', no such filter exists
2008-05-06 20:47:12.074 Couldn't load deinterlace filter none
2008-05-06 20:47:12.074 Failed to enable deinterlacing
2008-05-06 20:47:20.320 TV: Attempting to change from WatchingPreRecorded to None
2008-05-06 20:47:20.438 TV: Changing from WatchingPreRecorded to None
2008-05-06 20:47:20.635 DPMS Reactivated.
2008-05-06 20:47:23.952 AFD: Opened codec 0x8a3d4e0, id(MPEG2VIDEO) type(Video)
2008-05-06 20:47:23.952 AFD: codec MP3 has 2 channels
2008-05-06 20:47:23.952 AFD: Opened codec 0x88e1a50, id(MP3) type(Audio)
Starting mythfrontend.real..
2008-05-06 20:48:17.442 New DB connection, total: 2
2008-05-06 20:48:17.443 Connected to database 'mythconverg' at host: localhost
2008-05-06 20:48:17.449 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-05-06 20:48:17.449 Enabled verbose msgs:  important general
2008-05-06 20:48:17.839 Unable to parse themeinfo.xml for glass-wide
2008-05-06 20:48:17.840 The theme (glass-wide) is missing a themeinfo.xml file
2008-05-06 20:48:18.427 Unable to parse themeinfo.xml for glass-wide
2008-05-06 20:48:18.428 The theme (glass-wide) is missing a themeinfo.xml file
2008-05-06 20:48:18.925 Primary screen 0.
2008-05-06 20:48:18.926 Using screen 0, 1280x1024 at 0,0
2008-05-06 20:48:18.929 Switching to square mode (G.A.N.T)
2008-05-06 20:48:19.183 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2008-05-06 20:48:19.184 lirc_init failed for mythtv, see preceding messages
2008-05-06 20:48:19.185 JoystickMenuClient Error: Joystick disabled - Failed to read /home/sean/.mythtv/joystickmenurc
2008-05-06 20:48:21.948 Loading from: /usr/share/mythtv/themes/G.A.N.T/base.xml
2008-05-06 20:48:22.140 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-05-06 20:48:22.346 Registering Internal as a media playback plugin.
2008-05-06 20:48:22.832 MythMusic adding CD-Writer: 1,0,0 -- CD-RW  CRX230E 
2008-05-06 20:48:23.231 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2008-05-06 20:48:27.686 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-05-06 20:48:27.688 Using protocol version 40
2008-05-06 20:48:27.704 TV: Attempting to change from None to WatchingLiveTV
2008-05-06 20:48:27.705 Using protocol version 40
2008-05-06 20:48:29.674 DPMS Deactivated
2008-05-06 20:48:29.682 New DB connection, total: 3
2008-05-06 20:48:29.684 Connected to database 'mythconverg' at host: localhost
2008-05-06 20:48:29.727 NVP: Disabling Audio, params(-1,2,44100)
2008-05-06 20:48:29.921 VideoOutputXv: Falling back to X shared memory video output.
                  *** May be slow ***
2008-05-06 20:48:29.996 OSD Theme Dimensions W: 640 H: 480
2008-05-06 20:48:30.842 TV: Changing from None to WatchingLiveTV
2008-05-06 20:48:30.854 FilterManager: failed to load filter 'none', no such filter exists
2008-05-06 20:48:30.855 Couldn't load deinterlace filter none
2008-05-06 20:48:30.910 Realtime priority would require SUID as root.
2008-05-06 20:48:30.961 OpenGLVideoSync()
2008-05-06 20:48:31.193 ~OpenGLVideoSync() -- begin
2008-05-06 20:48:31.193 ~OpenGLVideoSync() -- middle
2008-05-06 20:48:31.193 ~OpenGLVideoSync() -- end
2008-05-06 20:48:31.195 Video timing method: USleep with busy wait
2008-05-06 20:48:32.867 VideoOutputXv: Falling back to X shared memory video output.
                  *** May be slow ***
2008-05-06 20:48:33.168 AFD: Opened codec 0x9c91510, id(MPEG2VIDEO) type(Video)
2008-05-06 20:48:33.169 AFD: codec MP3 has 2 channels
2008-05-06 20:48:33.170 AFD: Opened codec 0x9d06710, id(MP3) type(Audio)
2008-05-06 20:48:33.223 Opening audio device 'default'. ch 2(2) sr 48000
2008-05-06 20:48:33.223 Opening ALSA audio device 'default'.
2008-05-06 20:48:33.317 NVP: Enabling Audio
2008-05-06 20:48:36.038 VideoOutputXv Error:
***
* Your system is not capable of displaying the
* full framerate at 1280x1024 resolution.  Frames
* will be skipped in order to keep the audio and
* video in sync.

2008-05-06 20:48:55.179 TV: Attempting to change from WatchingLiveTV to None
2008-05-06 20:48:55.547 TV: Changing from WatchingLiveTV to None
2008-05-06 20:48:55.627 DPMS Reactivated.

```

---

### Post by volkswagner on 2008-05-06
From you log:

```

* Your system is not capable of displaying the
* full framerate at 1280x1024 resolution.  Frames
* will be skipped in order to keep the audio and
* video in sync.
```

Have you tried to lower your screen resolution?

---

### Post by laga on 2008-05-06
xshm == bad.

You probably need to set an option in the ATI driver to enable Xvideo support on the tv-out. The 'xv-blit' video renderer should work then.

---

### Post by tinny on 2008-05-06
> **laga said:**
> xshm == bad.

You probably need to set an option in the ATI driver to enable Xvideo support on the tv-out. The 'xv-blit' video renderer should work then.

Where can I set this option?

---

### Post by tinny on 2008-05-06
> **volkswagner said:**
> From you log:

```

* Your system is not capable of displaying the
* full framerate at 1280x1024 resolution.  Frames
* will be skipped in order to keep the audio and
* video in sync.
```

Have you tried to lower your screen resolution?

Do I lower this within Mythbuntu or in the xfce desktop?

(Sorry for the dumb question)

---

### Post by volkswagner on 2008-05-06
To change your resolution and the settings laga mentioned, go to your desktop.  You can open mythbuntu control center and go to the restricted drivers tab.  You should see ATI control center.  I would start with lagas recomendation.  If you are connected via s-vid, I think the best resolution would be 640x480.

EDIT:  If you do change your resolution, you may loose a portion of your desktop (tv overscan), can get annoying.  Just another reason for ssh.

I am not sure how well you can read your desktop at the moment.  Nor do I know how well you will be able to read it after resolution change.  Can you access your machine remote (ssh or vnc)?

For my setup, I use my laptop connect to my backend via ssh, since text is hard to read on my 26" CRT TV (640x480).

---

### Post by tinny on 2008-05-07
> **volkswagner said:**
> To change your resolution and the settings laga mentioned, go to your desktop.  You can open mythbuntu control center and go to the restricted drivers tab.  You should see ATI control center.  I would start with lagas recomendation.  If you are connected via s-vid, I think the best resolution would be 640x480.

EDIT:  If you do change your resolution, you may loose a portion of your desktop (tv overscan), can get annoying.  Just another reason for ssh.

I am not sure how well you can read your desktop at the moment.  Nor do I know how well you will be able to read it after resolution change.  Can you access your machine remote (ssh or vnc)?

For my setup, I use my laptop connect to my backend via ssh, since text is hard to read on my 26" CRT TV (640x480).
Ive got VNC setup.

I changed the resolution to 640x480 with no real improvement.

I could see the ATI control centre (ATI Catalyst Control Center???) button you talk about but it was disabled :-( , however I did have the nvidia control centre (thats no help).

So next I plan on figuring out how to install the ATI Catalyst Control Centre on Ubuntu and then ill work on those settings.

---

### Post by volkswagner on 2008-05-07
> **tinny said:**
> Ive got VNC setup.

I changed the resolution to 640x480 with no real improvement.

I could see the ATI control centre (ATI Catalyst Control Center???) button you talk about but it was disabled :-( , however I did have the nvidia control centre (thats no help).

So next I plan on figuring out how to install the ATI Catalyst Control Centre on Ubuntu and then ill work on those settings.

Are you sure the restricted drivers are enabled and in use?

---

### Post by tinny on 2008-05-07
> **volkswagner said:**
> Are you sure the restricted drivers are enabled and in use?

Yep, thats what the Restricted drivers manager is telling me.

I was planning on following this tutorial

[http://www.phoronix.com/forums/showthread.php?t=7193]("http://www.phoronix.com/forums/showthread.php?t=7193")

---

### Post by volkswagner on 2008-05-07
That is not recommended.  You should have the best performance with the MCC appointed drivers.  If you have a lot of time invested, backup you system.  Create an image of you system.  If you are not to far invested, by all means go ahead.  It is difficult to recover from malfunctioned display driver.

When you went into your display settings, what was the driver in use?

---

### Post by tinny on 2008-05-07
Can I just install the control center and not the drivers? And then use the drivers that where installed with my system?

(Ill get the driver name when I get home tonight)

Also, I have a new CDROM to install in my system. Maybe I should try a clean install that uses the Mythbuntu ISO??? 

Ive heard of problems with 8.04 Mythbuntu, should I try 7.10? If so what features will I lose???

Thanks :-)

---

### Post by tinny on 2008-05-09
OK so ive finally got this working ok, this is what I did.

I managed to get a working CD ROM installed, this meant that I could do a clean standard install of Mythbuntu 8.04.

After doing this I still had the video problems, however the sound is now working really well!

Next I enabled the proprietary ATI driver using the restricted hardware drivers manager.

Then I configured s-video and xvideo.

```

sudo aticonfig --overlay-on=0 --enable-monitor=tv --tv-format-type=PAL-B --tv-standard-type=VIDEO --overlay-type=Xv --desktop-setup=clone

```

This configured my /etc/X11/xorg.conf graphics related settings.

```

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	Option	    "OverlayOnCRTC2" "0"
	Option	    "EnableMonitor" "tv"
	Option	    "TVFormat" "PAL-B"
	Option	    "TVStandard" "VIDEO"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "DesktopSetup" "clone"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
EndSection

```

My TV playback settings in Mythbuntu are now:

Decoder: libmpeg2
Video Renderer: xv-blit
OSD Renderer: softblend
Primary Deinterlacer: linearblend
Fallback Deinterlcer: linearblend

This setup results in a very good picture quality with no video flicker :-).

There is still one problem remaining, the size of the video is incorrect and varies depending on whether or not a channel is wide screen or not (depends on the aspect ratio). I mostly get my video only taking up about 3/4 of the available screen size with a thick black boarder around the edge.

---

### Post by tinny on 2008-05-09
:) I HAVE IT WORKING PERFECT :)

I just changed the Aspect Ratio to "4:3" and the Zoom to "stretch" in my Mythbuntu Playback settings. It looks great!!!

Thanks for all the help!

---

