---
title: "Can't play DVDs I followed all the stickys"
date: 2009-04-21
forum: Multimedia Software
---

### Post by azebuski on 2009-04-21
I have read all the posts I can find, installed the Medibuntu repos, I have libdvdcss2, libdvdnav4, VLC, ubuntu-restricted-extras, and everything else installed.

If I try to play a DVD in Totem a dialog box pops up saying "The folder contents could not be displayed. Operation unsupported."

If I use VLC to play a disc it simply closes down. I ran VLC from the command line and got this when it automatically shut down.

```

libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: KEEPINGUPAPPEARANCES_D3
libdvdnav: DVD Serial Number: 2E3755AB
libdvdnav: DVD Title (Alternative): KEEPINGUPAPPEARANCES_D3
libdvdnav: Unable to find map file '/home/albert/.dvdnav/KEEPINGUPAPPEARANCES_D3.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0002a378
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0002d3dc
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x002dfa81
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 0
[00000460] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
ALSA lib setup.c:555:(add_elem) Cannot obtain info for CTL elem (MIXER,'IEC958 Playback Default',0,0,0): No such file or directory
[????????] x11 video output error: X11 request 132.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  81
  Current serial number in output stream:  82

```

What am I missing?

---

### Post by wolfen69 on 2009-04-21
how old is the installation of ubuntu? sounds like it is borked. i have never had a problem playing dvd's.

judging from the output above, it sounds like X is screwed up. google for "x11 video output error: X11 request 132.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)".

---

### Post by xc3RnbFO8P on 2009-04-21
Try this in terminal:
> gstreamer-properties
In VLC you can find it in Preferences> Video> output modules.

> Workaround to get it working: open gstreamer-properties. Then, Video tab, Default Output section. Change the Plugin from "Autodetect" to "X Window System (No Xv)" and close. This way, totem will play any video format.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/354688]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/354688")

---

### Post by azebuski on 2009-04-21
Thanks Ringi!  In VLC I changed my video output from "default" to "X11 video output" and DVDs are playing fine.

I tried changing the settings in gstreamer-properties but Totem still gives me the same error message. 

I don't mind, I prefer VLC anyway.

---

### Post by bturig on 2009-04-22
It worked for me. Thanks!

In VLC: Tools->Preferences->Video->Output to X11 Video Output.

and from the terminal gstreamer-properties->Video->Default Output->Plug In to X11 Window System (No Xv).

My symptoms were that I could not play any media files (mpeg, flvs)
Some how I screwed up my install upgrade. (Jaunty Beta)

---

### Post by dannyboy79 on 2009-12-23
didn't work for me. i changed VLC video out to X11 Video Output. and gstreamer-properties to X11 Window System (No Xv). but i still get this error when running this command from command line
vlc /dev/dvd

 vlc /dev/dvd
VLC media player 1.0.2 Goldeneye
[0x9532d98] main interface error: no interface module matched "globalhotkeys,none"
[0x9532d98] main interface error: no suitable interface module
[0x9496140] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x9496140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: DVDVIDEO
libdvdnav: DVD Serial Number: 4B306F1100000000
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/daniel/.dvdnav/DVDVIDEO.map'
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000123
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000148
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000008c1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0000090a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00000920
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 0
[0x9672c20] main input error: ES_OUT_RESET_PCR called
[0x9672c20] main input error: ES_OUT_RESET_PCR called
[0x9814b90] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:128000
[0x98f1ac0] pulse audio output: No. of Audio Channels: 2
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 143.3 failed with error code 8:
 BadMatch (invalid parameter attributes)
[????????] x11 video output notice: buggy X11 server claims shared memory
[????????] x11 video output notice: support though it does not work (OpenSSH?)
[????????] x11 video output error: X11 request 143.3 failed with error code 8:
 BadMatch (invalid parameter attributes)
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (MIT-SHM)
  Minor opcode of failed request:  3 (X_ShmPutImage)
  Serial number of failed request:  64
  Current serial number in output stream:

if i select the vob from nautilus, and open with mplayer, it works but the sound is off. i probably have some pulseaudio issue. 

when I use totem it works just fine.

---

### Post by mc4man on 2009-12-24
> when I use totem it works just fine

That might rule out display adapter/driver issues, do you have cairo-dock installed?
(The combo of vlc 1.0.2, cairo-dock and karmic don't work atm

edit:
[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/416294](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/416294)

---

### Post by bubbabear on 2009-12-24
I followed all the instructions to get dvds to mount but /dev/sr0 is empty when DVD is installed.  Try manual mount and that wouldn't work.  Audio CDs play.  Nvidia drivers were removed from this computer due to erratic behavior during booting.  Does not having the video drivers installed cause this problem?

---

### Post by dannyboy79 on 2009-12-24
> **bubbabear said:**
> I followed all the instructions to get dvds to mount but /dev/sr0 is empty when DVD is installed.  Try manual mount and that wouldn't work.  Audio CDs play.  Nvidia drivers were removed from this computer due to erratic behavior during booting.  Does not having the video drivers installed cause this problem?

most likely because your video card is what renders the video for playback. if you run a command like vlc /dev/dvd  what does it spit back at you. then with mplayer /dev/dvd or totem /dev/dvd

---

