---
title: "No access module matched &quot;dvd&quot;?"
date: 2009-12-14
forum: Multimedia Software
---

### Post by HellionDarkLord on 2009-12-14
What does that mean?

I have tried everything I can find and nothing works!  I have downloaded ind installed all the gstreamer plugins, libdvdcss, w64codecs, and nothing works.

So here is my output```
:~$ cvlc -v dvd://
VLC media player 1.0.2 Goldeneye
[0x20587c8] main demux warning: no access_demux module matching "file" could be loaded
[0x2073598] main interface error: no interface module matched "globalhotkeys,none"
[0x2073598] main interface error: no suitable interface module
[0x1f5f888] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x2073538] dummy interface: using the dummy interface module...
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: HEROES
libdvdnav: DVD Serial Number: 36dd9b75
libdvdnav: DVD Title (Alternative): SEASON_1_DISC_1_R1
libdvdnav: Unable to find map file '/home/gabriel/.dvdnav/HEROES.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000014d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000049f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00010e83
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x001e7b5c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001e7b60
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00369748
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0036974c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x0039af97
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0039af9b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x003aaf1c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x003aaf20
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x003ac886
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003ac88a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x003aea89
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x003aea8d
libdvdread: Elapsed time 0
libdvdread: Found 7 VTS's
libdvdread: Elapsed time 0
libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed
[0x2077188] dvdnav demux error: cannot set title (can't decrypt DVD?)
[0x2077188] main demux error: Playback failure
[0x2077188] main demux error: VLC cannot set the DVD's title. It possibly cannot decrypt the entire disc.
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Invalid title IFO (VTS_01_0.IFO).
[0x2077188] dvdread demux error: fatal error in vts ifo
[0x2077188] dvdread demux error: DvdReadSetArea(0,0,1) failed (can't decrypt DVD?)
[0x2077188] main demux warning: no access_demux module matching "dvd" could be loaded
[0x20c2b18] main access error: no access module matched "dvd"
[0x2077c58] main input error: open of `dvd://' failed: no access module matched "dvd"
[0x2077c58] main input error: Your input can't be opened
[0x2077c58] main input error: VLC is unable to open the MRL 'dvd://'. Check the log for details.


```

What is going on?  I've even reinstalled all the packages and nothing changed.

---

### Post by aciel on 2010-02-12
Bump. Same problem.

---

