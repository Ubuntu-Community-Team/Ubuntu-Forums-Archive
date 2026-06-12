---
title: "Can't get legal DVD to play"
date: 2009-02-14
forum: Multimedia Software
---

### Post by dinodeman on 2009-02-14
**SOLVED**
After installing libdvdcss2 I put another DVD inside and played it and then put Rendition back and it worked.

Hi Guys

I bought a movie on DVD called Rendition, but somehow it doesn't work with my Ubuntu installation. I tried it with Windows and then everything worked fine. But I don't want to watch it with Windows, I want to watch it with ubuntu :)
I already installed libdvdcss2 to be sure that it had nothing to do with encrypted DVD's. I use VLC to play the DVD and below you can see the output of VLC.
> 
VLC media player 0.8.6e Janus

** (.:6604): CRITICAL **: gtk_pizza_set_size: assertion `pizza != NULL' failed
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdnav: DVD Title: RENDITION
libdvdnav: DVD Serial Number: 483C123D___MVB__
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/remco/.dvdnav/RENDITION.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000016d
libdvdread: Elapsed time 2
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001f3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0002fb40
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0002fbdf
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0002fc2c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x000312b5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00031302
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x00031db2
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x00031dff
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x000336c1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x0003370e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x000349f1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x00034a3e
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x00034adb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x00034b28
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x0026aa4a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x0026aa97
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x00273f22
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x00273f6f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x002d3530
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x002d357d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_0.VOB at 0x0031da23
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x0031da70
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_0.VOB at 0x003912af
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_1.VOB at 0x003912fc
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_0.VOB at 0x0039ac36
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_1.VOB at 0x0039ac83
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_0.VOB at 0x003a1345
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_14_1.VOB at 0x003a1392
libdvdread: Elapsed time 0
libdvdread: Found 14 VTS's
libdvdread: Elapsed time 6
*** Zero check failed in ifo_read.c:926
    for vts_ptt_srpt->zero_1 = 0xd5b7

*** libdvdread: CHECK_VALUE failed in ifo_read.c:928 ***
*** for vts_ptt_srpt->nr_of_srpts < 100 ***

libdvdnav: ifoRead_VTS_PTT_SRPT failed - CRASHING!!!
vlc: vm.c:202: ifoOpenNewVTSI: Assertion `0' failed.
Aborted


I use ubuntu 8.04 with this kernel:
> 
remco@jupiter:~$ uname -a
Linux jupiter 2.6.24-23-generic #1 SMP Mon Jan 26 00:13:11 UTC 2009 i686 GNU/Linux


Does anybody recognize the problem and also knows the solution. Then please let me know.

---

### Post by hyper_ch on 2009-02-14
add medibuntu repos and then add the libdvdcss2 package

---

