---
title: "Watch TV black screens after working just one time"
date: 2008-10-19
forum: Mythbuntu
---

### Post by pokepoke on 2008-10-19
I'm running Mythbuntu 8.04.1 with two ATI HDTV cards and onboard sound card. When I start "Watch TV", the OSD comes up to tell me channel I'm on, but no picture appears. I was able to watch TV one time on this setup, but for some reason it no longer works, and I haven't even reset the computer. The frontend log is below:

```
Starting mythfrontend.real..
2008-10-19 13:54:32.836 New DB connection, total: 2
2008-10-19 13:54:32.837 Connected to database 'mythconverg' at host: localhost
2008-10-19 13:54:32.839 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-10-19 13:54:32.839 Enabled verbose msgs:  important general
2008-10-19 13:54:33.021 Unable to parse themeinfo.xml for glass-wide
2008-10-19 13:54:33.021 The theme (glass-wide) is missing a themeinfo.xml file
2008-10-19 13:54:33.400 Unable to parse themeinfo.xml for glass-wide
2008-10-19 13:54:33.401 The theme (glass-wide) is missing a themeinfo.xml file
2008-10-19 13:54:33.901 No theme dir: /home/bishop/.mythtv/themes/Mythbuntu-8.04
2008-10-19 13:54:33.903 Primary screen 0.
2008-10-19 13:54:33.904 Using screen 0, 1920x1080 at 0,0
2008-10-19 13:54:33.906 No theme dir: /home/bishop/.mythtv/themes/Mythbuntu-8.04
2008-10-19 13:54:33.907 Switching to square mode (Mythbuntu-8.04)
2008-10-19 13:54:33.929 Using the Qt painter
mythtv: could not connect to socket
mythtv: Connection refused
2008-10-19 13:54:33.930 lirc_init failed for mythtv, see preceding messages
2008-10-19 13:54:33.930 JoystickMenuClient Error: Joystick disabled - Failed to read /home/bishop/.mythtv/joystickmenurc
2008-10-19 13:54:36.110 Specified base font 'medium' does not exist for font clock
2008-10-19 13:54:36.110 Specified base font 'medium' does not exist for font small
2008-10-19 13:54:36.110 Specified base font 'medium' does not exist for font medium
2008-10-19 13:54:36.110 Specified base font 'medium' does not exist for font large
2008-10-19 13:54:36.111 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-10-19 13:54:36.331 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-10-19 13:54:36.374 Registering Internal as a media playback plugin.
2008-10-19 13:54:36.478 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-10-19 13:54:36.518 Failed to run 'cdrecord --scanbus'
2008-10-19 13:54:36.521 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-10-19 13:54:36.524 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-10-19 13:54:36.552 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.0.95:5060 NAT address 192.168.0.95
SIP: Cannot register; proxy, username or password not set
2008-10-19 13:54:36.647 Starting update of NDFD-6_day
2008-10-19 13:54:36.655 Starting update of NWS-Alerts
2008-10-19 13:54:36.663 Starting update of NWS-XML
2008-10-19 13:54:36.676 NetworkControl: Listening for remote connections on port 6546
2008-10-19 13:55:52.766 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-10-19 13:55:52.767 Using protocol version 40
2008-10-19 13:55:52.794 TV: Attempting to change from None to WatchingLiveTV
2008-10-19 13:55:52.795 Using protocol version 40
2008-10-19 13:55:53.966 NVP: Disabling Audio, params(-1,2,44100)
2008-10-19 13:55:54.041 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-10-19 13:55:54.117 OSD Theme Dimensions W: 640 H: 480
2008-10-19 13:55:55.662 TV: Changing from None to WatchingLiveTV
2008-10-19 13:55:55.672 Realtime priority would require SUID as root.
2008-10-19 13:55:55.771 Video sync method cant support double framerate (refresh rate too low for bob deint)
2008-10-19 13:55:55.773 Video timing method: USleep with busy wait
2008-10-19 13:55:56.831 VideoOutputXv: XvMC Adaptor Name: 'NV17 Video Texture'
2008-10-19 13:55:57.693 VideoOutputXv: ProcessFrameXvMC: Tried to reuse frame but failed
2008-10-19 13:55:57.694 VideoOutputXv: ProcessFrameXvMC: Called without frame
2008-10-19 13:55:57.695 AFD: Opened codec 0x93db0f0, id(MPEG2VIDEO_XVMC) type(Video)
2008-10-19 13:55:57.695 AFD: codec AC3 has 6 channels
2008-10-19 13:55:57.697 AFD: Opened codec 0x93da9a0, id(AC3) type(Audio)
2008-10-19 13:55:57.860 VideoOutputXv: ProcessFrameXvMC: Tried to reuse frame but failed
2008-10-19 13:55:57.861 VideoOutputXv: ProcessFrameXvMC: Called without frame
2008-10-19 13:55:57.996 Opening audio device 'default'. ch 6(2) sr 48000
2008-10-19 13:55:57.997 Opening ALSA audio device 'default'.
2008-10-19 13:55:58.027 VideoOutputXv: ProcessFrameXvMC: Tried to reuse frame but failed
2008-10-19 13:55:58.027 VideoOutputXv: ProcessFrameXvMC: Called without frame
ALSA lib confmisc.c:768:(parse_card) cannot find card '3'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM spdif
2008-10-19 13:55:58.052 AudioOutput Error: snd_pcm_open(default): No such file or directory
2008-10-19 13:55:58.052 NVP: Disabling Audio, reason is: snd_pcm_open(default): No such file or directory
2008-10-19 13:55:58.114 XvMC: picture structure FRAME
2008-10-19 13:55:58.294 NVP: Prebuffer wait timed out 10 times.
2008-10-19 13:55:59.624 NVP: Prebuffer wait timed out 10 times.
2008-10-19 13:56:00.954 NVP: Prebuffer wait timed out 10 times.
```

Any help would be greatly appreciated.

---

### Post by somersetsimon on 2008-10-28
> **pokepoke said:**
> I'm running Mythbuntu 8.04.1 with two ATI HDTV cards and onboard sound card. When I start "Watch TV", the OSD comes up to tell me channel I'm on, but no picture appears. I was able to watch TV one time on this setup, but for some reason it no longer works, and I haven't even reset the computer. The frontend log is below:


I seem to have exactly the same problem. After a few hours of fiddling around with drivers and firmware, I got my Hauppauge Nova-T USB stick up and running. The backend setup seems to go ok and the device is picked up. One problem is that I don't seem to be able to pick up any EPG information. When I select the frontend and Watch Live TV I get the bottom half of the screen with channel info (in very poor picture quality) and no TV picture (or sound).
Any clues? I know the signal should be ok as we can receive Freeview with no problem at all. I'm running Mythbuntu 8.04 on a Toshiba Tecra M1 with a Trident Cyberblade video card.
Where do you find your frontend log?

Thanks
Simon

---

### Post by pokepoke on 2008-11-01
I don't know. I was able to fix my situation by removing and reinstalling the Nvidia non-free drivers for my video card.

---

