---
title: "Encryption problems, help needed!"
date: 2010-02-10
forum: Multimedia Software
---

### Post by rasmus91 on 2010-02-10
Hi there.

Been using 40 minutes or so trying to be able to watch Final Fantasy 7 Advent Children on my laptop. It's a bought dvd so there shouldn't be any problems with the disc like bad quality or so.

I've been searching the web thin for solutions, and i have installed the libdvdcss2 and a lot of other libraries, but i'm totally unable to watch the dvd vlc player instantly crashes when trying to play the DVD

I ran it in a terminal just to get this error code:

```
vlc
VLC media player 1.0.2 Goldeneye
[0x18c6cf8] main interface: creating httpd
[0x17b6888] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Attempting to use device /dev/sr0 mounted on /media/FINAL_FANTASY_VII for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/rasmus/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00e50000. Regions: 2 4 5

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x000001cd
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000019df
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00047e71
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x002c5c68
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x002c5cb5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00311369
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x003113b6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x0035ca07
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0035ca54
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x003e5c2a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x003e5c77
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x003e7049
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003e7096
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x003eb646
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x003eb693
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x003ec598
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x003ec5e5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x003ecea4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x003ecef1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x003efa7e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x003efacb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_0.VOB at 0x003f00b7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x003f0104
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_0.VOB at 0x003f07de
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_1.VOB at 0x003f082b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_0.VOB at 0x003f0f0a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_1.VOB at 0x003f0f57
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_0.VOB at 0x003f1154
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_1.VOB at 0x003f11a1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_0.VOB at 0x003f1621
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_1.VOB at 0x003f166e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_16_0.VOB at 0x003f1b83
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_16_1.VOB at 0x003f1bd0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_17_0.VOB at 0x003f20a1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_17_1.VOB at 0x003f20ee
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_18_0.VOB at 0x003f2643
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_18_1.VOB at 0x003f2690
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_19_0.VOB at 0x003f2b52
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_19_1.VOB at 0x003f2b9f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_20_0.VOB at 0x003f312b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_20_1.VOB at 0x003f3178
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_21_0.VOB at 0x003f3796
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_21_1.VOB at 0x003f37e3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_22_0.VOB at 0x003f3b99
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_22_1.VOB at 0x003f3be6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_23_0.VOB at 0x003f417e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_23_1.VOB at 0x003f41cb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_24_0.VOB at 0x003f481d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_24_1.VOB at 0x003f486a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_25_0.VOB at 0x003f4cf0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_25_1.VOB at 0x003f4d3d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_26_0.VOB at 0x003f537f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_26_1.VOB at 0x003f53cc
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_27_0.VOB at 0x003f599d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_27_1.VOB at 0x003f59ea
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_28_0.VOB at 0x003f5ff2
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_28_1.VOB at 0x003f603f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_29_0.VOB at 0x003f6604
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_29_1.VOB at 0x003f6651
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_30_0.VOB at 0x003f6ba8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_30_1.VOB at 0x003f6bf5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_31_0.VOB at 0x003f716e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_31_1.VOB at 0x003f71bb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_32_0.VOB at 0x003f767f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_32_1.VOB at 0x003f76cc
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_33_0.VOB at 0x003f7c6d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_33_1.VOB at 0x003f7d85
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_34_0.VOB at 0x003f9f9e
libdvdread: Elapsed time 0
libdvdread: Found 33 VTS's
libdvdread: Elapsed time 0
*** Zero check failed in ifo_read.c:810
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:810
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:810
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:810
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:810
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:810
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:810
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:810
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:810
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:810
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:810
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:810
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:810
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:810
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:810
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:810
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:810
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:810
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:810
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:810
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:810
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:810
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:810
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:810
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:810
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:810
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:810
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:810
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:810
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:810
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:810
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:810
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:810
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:810
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:810
    for cell_position[i].zero_1 = 0x04
libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed
vlc: /build/buildd/libdvdnav-4.1.3/src/vm/vm.c:1485: process_command: Assertion `0' failed.
Aborted

```

sorry, i don't have enough patience to keep trying for my self.

As this is one of my favorite DVD's, i'd really like to be able to watch it.

Thanks for any help. (the faster the better ;) )

---

### Post by rasmus91 on 2010-02-10
OMG!!! i guess sometimes all it takes is a f****** restart.

Sorry guys! i guess my frustration took over!

Have a nice day!

---

