---
title: "xine dvd playback failure"
date: 2009-05-07
forum: Multimedia Software
---

### Post by schizostatic on 2009-05-07
I have been wrestling with dvd playback for awhile and so far xine is the closest I get. I toss in a dvd, run xine and I get this in the terminal first
> joe@joe-laptop:~$ xine
This is xine (X11 gui) - a free video player v0.99.6cvs.
(c) 2000-2007 The xine Team.
libdvdread: Using libdvdcss version 1.2.10 for DVD access

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x000002c0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00007180
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0005af3b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x002c0220
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x002c0240
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x002c03c0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002c03e0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x002f1840
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x002f1860
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x003064a0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x003064c0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x0030dca0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x0030dcc0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x00316820
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x00316840
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x00322e40
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x00337080
libdvdread: Elapsed time 0
libdvdread: Found 8 VTS's
libdvdread: Elapsed time 0


The opening sequence runs for the dvd for the company/whatnot. Then it chokes and says
[IMG]http://www.imageput.com/hosted/34366screenshot.png[/IMG]

I have both libdvdcss2 and libdvdnav4 and libdvdread4 installed. Any ideas?

---

### Post by fox123 on 2009-10-18
I had the same problem. This worked for me. 
1. Install libdvdcss.
2. Go to the **xine setup** and click on the "**media**" tab
3. go down to the "**Device used for DVD playback**" and change it from **/dev/dvd** to **/media/dvd** or **media/cdrom** 
 or whatever your dvd is called.
4. restart xine

This is the first time I had to make this change. xine usually works just fine without it, 
but for some reason xine couldn't read the dvd listed as /dev/dvd.
I hope this helps.

---

### Post by vinutux on 2009-10-19
Try Mplayer or vlc

---

