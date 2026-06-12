---
title: "Shoot 'em Up kills VLC"
date: 2008-03-28
forum: Multimedia &amp; Video
---

### Post by djrobthaman on 2008-03-28
Hi,

I can play all my other dvds on vlc but shoot em up makes it crash immediately.  Anybody know what could be the problem?

Thanks

Terminal Output:
```

douglas@douglas-desktop:~$ vlc
VLC media player 0.8.6c Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: SHOOT_EM_UP
libdvdnav: DVD Serial Number: 376f5a4b
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/douglas/.dvdnav/SHOOT_EM_UP.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000288
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000036e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000230ab
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001fd840
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0021f1da
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x00233d1f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x00235edd
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x002363e9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x0025f8ec
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x0026a883
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x0034cce7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x0034d1f3
libdvdread: Elapsed time 0
libdvdread: Found 8 VTS's
libdvdread: Elapsed time 0
libdvdnav: ifoRead_VOBU_ADMAP vtsi failed - CRASHING
vlc: vm.c:214: ifoOpenNewVTSI: Assertion `0' failed.
Aborted (core dumped)

```

---

### Post by djrobthaman on 2008-03-28
Update:  If I try and open it in movie player I get a message that says I do not have the appropriate drivers to watch the dvd.  I just tested fight club in vlc and it works fine, so it's not dvds in general.  Is there a new encoding scheme or somthing I need to download a driver for?  does anybody know where I could find that?

---

### Post by mc4man on 2008-03-28
that title has x-protect type of structure protection. It can be handled in a couple of ways - for mplayer [http://ubuntuforums.org/showthread.php?t=652528&page=2](http://ubuntuforums.org/showthread.php?t=652528&page=2)
For vlc  [http://ubuntuforums.org/showthread.php?t=727671&page=2](http://ubuntuforums.org/showthread.php?t=727671&page=2) - replacing your libdvdnav.so.4.0.0 with the patched one is more convenient - I initially  went with dl'ing the patched .so to desktop and using it as a preload for vlc, then used it to replace the existing one. (first running chmod +x on it )  Either way works fine, method described by acirilo should be easier.

edit:i don't have movie player installed on gutsy - the vlc method may work, may not

---

