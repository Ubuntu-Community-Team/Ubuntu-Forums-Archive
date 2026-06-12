---
title: "[SOLVED] No DVD Playback; xine, Totem show errors"
date: 2008-07-03
forum: Multimedia Software
---

### Post by dbsoundman on 2008-07-03
I have done everything on the Comprehensive Multimedia How-To in terms of getting DVD playback going, and I even did region set to make sure my disc drive was set to Region 1. However, whenever I try to play a DVD, in xine I think I can get the Columbia logo playback, but when it gets to the menu it stops, citing an "Error reading NAV packet", and in Totem, it says "Could Not Read from Resource". I am out of ideas, I do not know what I should do. Help would be greatly appreciated. I'm on a fresh install (new computer) Hardy Heron 8.04.

I should also note that playback of any type of video on gxine is really really bad; it skips constantly. It's kind of like there's a DJ scratching the video, it's all over the place, and gets progressively worse as the video goes on. Audio is fine though.

Thanks,
Dan

---

### Post by dbsoundman on 2008-07-03
Ok, I just tried vlc, here's the output I get. In the case of this program, I can get to the main navigation menu, but when I click play it stops.

```
dan@blackdiamond:~$ vlc
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: SCHOOL_OF_ROCK_16X9
libdvdnav: DVD Serial Number: 30307D04
libdvdnav: DVD Title (Alternative): SCHOOL_OF_ROCK_16X9
libdvdnav: Unable to find map file '/home/dan/.dvdnav/SCHOOL_OF_ROCK_16X9.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000e6ec
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000e8c2
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000e945
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0000e95c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x000108df
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0001e4bd
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x000200b8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x000304f3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x002c4c1e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003a2e47
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x003b332b
libdvdread: Elapsed time 0
libdvdread: Found 7 VTS's
libdvdread: Elapsed time 0
libdvdnav: Suspected RCE Region Protection!!!
[00000342] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
[00000289] main playlist: nothing to play

```

-Dan

---

### Post by dbsoundman on 2008-07-03
I don't know what I did, but I tried some things and restarted, and now it works. I am starting a new thread though because playback, especially in fullscreen, is really choppy, and should not be...

-Dan

---

