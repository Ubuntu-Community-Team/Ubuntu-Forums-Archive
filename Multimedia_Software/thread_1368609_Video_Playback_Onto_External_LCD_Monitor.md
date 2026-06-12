---
title: "Video Playback Onto External LCD Monitor"
date: 2009-12-30
forum: Multimedia Software
---

### Post by dwhitney67 on 2009-12-30
Hi folks...

I recently complemented my laptop computer with an external 20" LCD monitor, and as far as day-to-day usage of my system, it works great.

However I have discovered that VLC, nor MPlayer Media Player, are able to display video from DVD disks or ISO images onto the external monitor.  If I open the laptop's monitor, then it plays fine onto the laptop's LCD screen, but nothing on the external monitor. 

The audio is played back without any issues.  Does anyone have a similar setup as I do, but with a working VLC and/or MPlayer?  Is there anything that can explain the issue with my system?

Below is the output produced by VLC when I ran it from the command line, and a screenshot, for what it is worth, of VLC in action, yet with the blank video screen as the video is playing.
```

vlc dvd:///dev/sr0
VLC media player 1.0.2 Goldeneye
[0x9109c18] main interface error: no interface module matched "globalhotkeys,none"
[0x9109c18] main interface error: no suitable interface module
[0x906b140] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x906b140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: MOFH
libdvdnav: DVD Serial Number: 2C5B4B46
libdvdnav: DVD Title (Alternative): MOFH
libdvdnav: Unable to find map file '/home/whitney/.dvdnav/MOFH.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00004d60
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000050a4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00005115
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0000512e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0000519f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x0005f6dd
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0005f74e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x0006f7ee
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0006f85f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x000af7eb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x000d62dc
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x00355acd
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x00355b3e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x003bb550
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x003bb5c1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x003bf09d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x003bffce
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x003c003f
libdvdread: Elapsed time 0
libdvdread: Found 9 VTS's
libdvdread: Elapsed time 0
libdvdnav: Suspected RCE Region Protection!!!
libdvdnav: Suspected RCE Region Protection!!!
[0x9355648] main input error: ES_OUT_RESET_PCR called
[0x9355648] main input error: ES_OUT_RESET_PCR called
[0x939ebc0] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
[0x93d2260] pulse audio output: No. of Audio Channels: 2
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1

```

P.S.  I am running Ubuntu 9.10

---

### Post by dwhitney67 on 2009-12-30
Nevermind... I found a solution; at least I think so.

I had to go to System -> Preferences -> Display, unselect "Mirror Screens" and select the Apply button.

This altered my screen setup momentarily, perhaps with a prompt on my laptop screen which I could not see (it is closed), and then within moments the display setup reverted to the "Mirror Screens" configuration automatically.

From this point on, the video was visible within VLC.  Whatever; I have really no desire to understand this fluke in the universe.  All I care is that it is now working.

---

### Post by ubusk8tr on 2010-04-09
n00bie here... sorry, but unselecting mirror alone did not work for me.

What I had to do was:
System/Preferences/Display - uncheck mirror - 
Highlight laptop screen and set it to **OFF**

Now VLC videos will play on my external monitor. I also checked un-docking my laptop and the 'native' laptop display is normal. Re-docking shows that the settings were saved and everything is working great :)

---

