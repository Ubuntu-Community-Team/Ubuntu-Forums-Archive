---
title: "Karmic DVD crashes"
date: 2009-11-01
forum: Multimedia Software
---

### Post by swatsbiz on 2009-11-01
Installed fresh Karmic Koala, but when I try to play a DVD in any of the media players it just crashes out, here's the output of vlc:

```
$ vlc
VLC media player 1.0.2 Goldeneye
[0x872a5d0] main interface error: no interface module matched "globalhotkeys,none"
[0x872a5d0] main interface error: no suitable interface module
[0x867f140] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x867f140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: KUNG_FU_PANDA
libdvdnav: DVD Serial Number: 392abbf9
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/sholah/.dvdnav/KUNG_FU_PANDA.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000018a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000266
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00000319
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x000003f5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x000004a8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x0004c603
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0004c6e1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x0004c7c9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0004c87c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x0004f317
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x0004f3ca
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x0004f798
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x0004f84b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x00056143
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x000561f6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x0005e670
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x0005e723
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x0006232b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x000623de
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x00062804
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x00089284
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_0.VOB at 0x00297e9b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x00297f4e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_0.VOB at 0x0029ba44
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_1.VOB at 0x0029baf7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_0.VOB at 0x002a2018
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_1.VOB at 0x002a20cb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_0.VOB at 0x002a88d4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_1.VOB at 0x002a8987
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_0.VOB at 0x002af734
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_1.VOB at 0x002af89a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_16_0.VOB at 0x002c89fa
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_16_1.VOB at 0x002c8aad
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_17_0.VOB at 0x002ce283
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_17_1.VOB at 0x002ce336
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_18_0.VOB at 0x002f4ec7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_18_1.VOB at 0x002f4f7a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_19_0.VOB at 0x002f89b6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_19_1.VOB at 0x002f8a69
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_20_0.VOB at 0x002f8b41
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_20_1.VOB at 0x002fad3c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_21_0.VOB at 0x003016d2
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_21_1.VOB at 0x00301785
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_22_0.VOB at 0x00303688
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_22_1.VOB at 0x0030373b
libdvdread: Elapsed time 0
libdvdread: Found 22 VTS's
libdvdread: Elapsed time 0
[0x897ac78] main input error: ES_OUT_RESET_PCR called
[0x897ac78] main input error: ES_OUT_RESET_PCR called
[0x8a95f78] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[0x8a7c3b8] pulse audio output: No. of Audio Channels: 2
[????????] x11 video output error: X11 request 132.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  106
  Current serial number in output stream:  107


```

What am I missing?

David

---

