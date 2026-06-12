---
title: "Sound mixer problem...?"
date: 2008-08-08
forum: Mythbuntu
---

### Post by tinny on 2008-08-08
Hi, my Mythbuntu setup is almost perfect. :guitar: but :(

I am unable to control the volume of my Mythbuntu setup.

I am running Mythbuntu 8.0.4. I think I have a mixer setup problem?

Here is the output of my frontend log while running the frontend and trying to adjust the volume.

```

Starting mythfrontend.real..
2008-08-09 11:37:32.439 New DB connection, total: 2
2008-08-09 11:37:32.440 Connected to database 'mythconverg' at host: localhost
2008-08-09 11:37:32.446 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-08-09 11:37:32.447 Enabled verbose msgs:  important general
2008-08-09 11:37:32.687 Unable to parse themeinfo.xml for glass-wide
2008-08-09 11:37:32.687 The theme (glass-wide) is missing a themeinfo.xml file
2008-08-09 11:37:33.035 Unable to parse themeinfo.xml for glass-wide
2008-08-09 11:37:33.035 The theme (glass-wide) is missing a themeinfo.xml file
2008-08-09 11:37:33.619 Primary screen 0.
2008-08-09 11:37:33.620 Using screen 0, 1024x768 at 0,0
2008-08-09 11:37:33.625 Switching to square mode (Mythbuntu-8.04)
2008-08-09 11:37:33.891 Using the Qt painter
2008-08-09 11:37:33.895 lirc init success using configuration file: /home/sean/.mythtv/lircrc
2008-08-09 11:37:33.895 JoystickMenuClient Error: Joystick disabled - Failed to read /home/sean/.mythtv/joystickmenurc
2008-08-09 11:37:38.395 Specified base font 'medium' does not exist for font clock
2008-08-09 11:37:38.395 Specified base font 'medium' does not exist for font small
2008-08-09 11:37:38.396 Specified base font 'medium' does not exist for font medium
2008-08-09 11:37:38.396 Specified base font 'medium' does not exist for font large
2008-08-09 11:37:38.400 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-08-09 11:37:38.554 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-08-09 11:37:38.739 Registering Internal as a media playback plugin.
2008-08-09 11:37:38.928 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-08-09 11:37:39.058 Failed to run 'cdrecord --scanbus'
2008-08-09 11:37:39.070 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-08-09 11:37:39.084 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-08-09 11:37:39.191 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.1.2:5060 NAT address 192.168.1.2
SIP: Cannot register; proxy, username or password not set
2008-08-09 11:37:48.689 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-08-09 11:37:48.692 Using protocol version 40
2008-08-09 11:37:48.731 TV: Attempting to change from None to WatchingLiveTV
2008-08-09 11:37:48.733 Using protocol version 40
2008-08-09 11:37:51.158 New DB connection, total: 3
2008-08-09 11:37:51.159 Connected to database 'mythconverg' at host: localhost
2008-08-09 11:37:51.201 DPMS Deactivated 
2008-08-09 11:37:51.217 NVP: Disabling Audio, params(-1,2,44100)
2008-08-09 11:37:51.416 VideoOutputXv: XVideo Adaptor Name: 'ATI Radeon Video Overlay'
2008-08-09 11:37:51.534 OSD Theme Dimensions W: 640 H: 480
2008-08-09 11:37:52.491 TV: Changing from None to WatchingLiveTV
2008-08-09 11:37:52.529 Realtime priority would require SUID as root.
2008-08-09 11:37:52.608 Video timing method: USleep with busy wait
2008-08-09 11:37:54.714 VideoOutputXv: XVideo Adaptor Name: 'ATI Radeon Video Overlay'
2008-08-09 11:37:55.094 AFD: Opened codec 0x8d725d0, id(MPEG2VIDEO) type(Video)
2008-08-09 11:37:55.094 AFD: codec MP3 has 2 channels
2008-08-09 11:37:55.095 AFD: Opened codec 0x8d73880, id(MP3) type(Audio)
2008-08-09 11:37:55.173 Opening audio device 'default'. ch 2(2) sr 48000
2008-08-09 11:37:55.173 Opening ALSA audio device 'default'.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL /dev/mixer
2008-08-09 11:37:55.211 AudioOutput Warning: Mixer attach error -2: No such file or directory
			Check Mixer Name in Setup: '/dev/mixer'
2008-08-09 11:37:55.213 NVP: Enabling Audio
2008-08-09 11:37:55.413 NVP: Prebuffer wait timed out 10 times.
2008-08-09 11:38:16.978 WriteAudio: buffer underrun
2008-08-09 11:38:17.023 WriteAudio: buffer underrun
2008-08-09 11:38:17.291 NVP: prebuffering pause
2008-08-09 11:38:20.383 NVP: Timed out waiting for free video buffers.
2008-08-09 11:38:21.010 WriteAudio: buffer underrun
2008-08-09 11:38:21.153 NVP: prebuffering pause
2008-08-09 11:38:25.630 TV: Attempting to change from WatchingLiveTV to None
2008-08-09 11:38:26.277 TV: Changing from WatchingLiveTV to None
2008-08-09 11:38:26.352 DPMS Reactivated.
Destroying SipFsm object 

```

Here is some more information about my system:

```

mythbuntu:~$ lspci
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

and

```

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

Any suggestions?

---

### Post by n8kraft on 2008-08-16
same problem except mythbuntu crashes for me when I choose "watch tv"

```
2008-08-16 16:21:14.924 AFD: Opened codec 0x85258c0, id(MPEG2VIDEO) type(Video)
2008-08-16 16:21:14.924 AFD: codec MP2 has 2 channels
2008-08-16 16:21:14.925 AFD: Opened codec 0x83858e0, id(MP2) type(Audio)
2008-08-16 16:21:15.046 Opening audio device 'default'. ch 2(2) sr 48000
2008-08-16 16:21:15.046 Opening ALSA audio device 'default'.
2008-08-16 16:21:15.121 mixer set channel 0 err -22: Invalid argument
2008-08-16 16:21:15.123 Mixer unable to find control Master 1
2008-08-16 16:21:15.124 mixer unable to find control Master 1
2008-08-16 16:21:15.137 Mixer unable to find control Master 1
2008-08-16 16:21:15.138 Mixer unable to find control Master 1
Segmentation fault
```

---

### Post by Dewey_Oxberger on 2008-08-19
I have a similar problem.  I can not control the volume and the audio is totally garbled (kind of like white noise).

I notice the:

(snd_ctl_open_noupdate) Invalid CTL /dev/mixer

along with

Mixer attach error -2: No such file or directory.

---

### Post by Dewey_Oxberger on 2008-08-19
Can't adjust the volume in mythtv?  Got static (white noise) in mythtv?  It's probably and audio setup problem.

In mythfrontend make your way to the main menu (the menu with Watch TV on it) and go to:

Utilities/Setup -- Setup -- General

Hit "Next" a few times to get to the tab labeled "Audio" in the upper left corner.

The configuration bits should all be there.

A little tinkering will go a long way  :)

For me the config is:

ALSA:Default

Default

Stereo .... Passive

x - Use internal volume controls

ALSA:default ....  Master

That got it working.

---

### Post by Dewey_Oxberger on 2008-08-19
That was ALSA : Default - not the ALSA:Default - those darn smilies...

---

### Post by tinny on 2008-08-20
> **Dewey_Oxberger said:**
> That was ALSA : Default - not the ALSA:Default - those darn smilies...

Unfortunately for me this didn't fix the problem :(

---

### Post by tinny on 2008-08-23
bump...

No one has a glue? Cant be that hard :) Maybe ive given too much info in the OP?

---

### Post by tinny on 2008-11-18
I still have this problem.

Maybe someone could provide me with a link to some sort of generic fault finding tips for MythTV sound...?

---

### Post by fosezzle on 2008-12-09
I struggled with this all afternoon but have managed to find a solution.

In alsamixer, I found that Mythbuntu was muting a couple of things. I unmuted everything and it didn't help. Then I found this (several hours later); [http://alsa.opensrc.org/index.php/FAQ#My_ALSA_modules_seem_to_be_loaded_fine_but_I_hear_no_sound._Why.27s_that.3F](http://alsa.opensrc.org/index.php/FAQ#My_ALSA_modules_seem_to_be_loaded_fine_but_I_hear_no_sound._Why.27s_that.3F)

which states that the SiS SI7012 card needs to have the IEC958 bits muted, and that some sound cards also require the Headphone bit to be muted. I muted both of these (by hitting 'm'), but did a little more testing and found that only the Headphone bit needs muting. Either way, play around and I hope this helps.

---

