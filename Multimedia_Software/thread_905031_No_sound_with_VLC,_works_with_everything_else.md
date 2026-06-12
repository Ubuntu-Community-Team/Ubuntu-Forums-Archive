---
title: "No sound with VLC, works with everything else"
date: 2008-08-29
forum: Multimedia Software
---

### Post by asenine on 2008-08-29
Thanks to the help of blackopus on #ubuntu, I have managed to get VLC to play protected discs. However, there is no sound. Sound is working fine on the rest of my system.

Here is the output:

```
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: <Vantage Point>
libdvdnav: DVD Serial Number: 38b186bb
libdvdnav: DVD Title (Alternative): Vantage Point
libdvdnav: Unable to find map file '/home/chris/.dvdnav/<Vantage Point>.map'
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000200
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0001bd4c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0003b975
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x002dfeb5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x002dff02
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x0035a935
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0035a982
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x003a3e09
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x003a3e56
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x003a7537
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x003a7584
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x003af08e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003af0db
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x003baed8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x003baf25
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x003c6922
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x003c696f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x003c7d41
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x003c7d8e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x003c8d29
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x003c8d76
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_0.VOB at 0x003cc007
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x003cc054
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_0.VOB at 0x003cc2de
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_1.VOB at 0x003cc32b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_0.VOB at 0x003cfbfb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_1.VOB at 0x003cfc48
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_0.VOB at 0x003d0317
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_1.VOB at 0x003d0364
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_0.VOB at 0x003d0b26
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_1.VOB at 0x003d0b73
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_16_0.VOB at 0x003d11ab
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_16_1.VOB at 0x003d11f8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_17_0.VOB at 0x003d192d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_17_1.VOB at 0x003d197a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_18_0.VOB at 0x003d202e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_18_1.VOB at 0x003d207b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_19_0.VOB at 0x003d2673
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_19_1.VOB at 0x003d26c0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_20_0.VOB at 0x003d2c74
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_20_1.VOB at 0x003d2cc1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_21_0.VOB at 0x003d3266
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_21_1.VOB at 0x003d32b3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_22_0.VOB at 0x003d3922
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_22_1.VOB at 0x003d396f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_23_0.VOB at 0x003d3fea
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_23_1.VOB at 0x003d4037
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_24_0.VOB at 0x003d475c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_24_1.VOB at 0x003d47a9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_25_0.VOB at 0x003d4e94
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_25_1.VOB at 0x003d4ee1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_26_0.VOB at 0x003d551b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_26_1.VOB at 0x003d5568
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_27_0.VOB at 0x003d5b8d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_27_1.VOB at 0x003d5bda
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_28_0.VOB at 0x003d6236
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_28_1.VOB at 0x003d6283
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_29_1.VOB at 0x003d6828
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_30_1.VOB at 0x003d6889
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_31_1.VOB at 0x003d9efb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_32_1.VOB at 0x003dba88
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_33_1.VOB at 0x003ea185
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_34_1.VOB at 0x003ebf9e
libdvdread: Elapsed time 0
libdvdread: Found 34 VTS's
libdvdread: Elapsed time 0
[00000343] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
[00000381] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000
libdvdnav: Suspected RCE Region Protection!!!
[00000389] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
[00000398] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:384000
[00000407] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:384000
[00000416] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:384000

```

And here is the output when I do what [this](http://ubuntuforums.org/showpost.php?p=5351569&postcount=5) post says:

```
0000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
libdvdread: Get key for /VIDEO_TS/VTS_13_0.VOB at 0x003cfbfb
libdvdread: Elapsed time 0
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
libdvdread: Get key for /VIDEO_TS/VTS_13_1.VOB at 0x003cfc48
libdvdread: Elapsed time 0
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
libdvdread: Get key for /VIDEO_TS/VTS_14_0.VOB at 0x003d0317
libdvdread: Elapsed time 0
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
libdvdread: Get key for /VIDEO_TS/VTS_14_1.VOB at 0x003d0364
libdvdread: Elapsed time 0
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
libdvdread: Get key for /VIDEO_TS/VTS_15_0.VOB at 0x003d0b26
libdvdread: Elapsed time 0
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
libdvdread: Get key for /VIDEO_TS/VTS_15_1.VOB at 0x003d0b73
libdvdread: Elapsed time 0
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
libdvdread: Get key for /VIDEO_TS/VTS_16_0.VOB at 0x003d11ab
libdvdread: Elapsed time 0
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
libdvdread: Get key for /VIDEO_TS/VTS_16_1.VOB at 0x003d11f8
libdvdread: Elapsed time 0
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
libdvdread: Get key for /VIDEO_TS/VTS_17_0.VOB at 0x003d192d
libdvdread: Elapsed time 0
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
libdvdread: Get key for /VIDEO_TS/VTS_17_1.VOB at 0x003d197a
libdvdread: Elapsed time 0
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
libdvdread: Get key for /VIDEO_TS/VTS_18_0.VOB at 0x003d202e
libdvdread: Elapsed time 0
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
libdvdread: Get key for /VIDEO_TS/VTS_18_1.VOB at 0x003d207b
libdvdread: Elapsed time 0
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
libdvdread: Get key for /VIDEO_TS/VTS_19_0.VOB at 0x003d2673
libdvdread: Elapsed time 0
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
libdvdread: Get key for /VIDEO_TS/VTS_19_1.VOB at 0x003d26c0
libdvdread: Elapsed time 0
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
libdvdread: Get key for /VIDEO_TS/VTS_20_0.VOB at 0x003d2c74
libdvdread: Elapsed time 1
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
libdvdread: Get key for /VIDEO_TS/VTS_20_1.VOB at 0x003d2cc1
libdvdread: Elapsed time 0
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
libdvdread: Get key for /VIDEO_TS/VTS_21_0.VOB at 0x003d3266
libdvdread: Elapsed time 0
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
libdvdread: Get key for /VIDEO_TS/VTS_21_1.VOB at 0x003d32b3
libdvdread: Elapsed time 0
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
libdvdread: Get key for /VIDEO_TS/VTS_22_0.VOB at 0x003d3922
libdvdread: Elapsed time 0
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
libdvdread: Get key for /VIDEO_TS/VTS_22_1.VOB at 0x003d396f
libdvdread: Elapsed time 0
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
libdvdread: Get key for /VIDEO_TS/VTS_23_0.VOB at 0x003d3fea
libdvdread: Elapsed time 0
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
libdvdread: Get key for /VIDEO_TS/VTS_23_1.VOB at 0x003d4037
libdvdread: Elapsed time 0
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
libdvdread: Get key for /VIDEO_TS/VTS_24_0.VOB at 0x003d475c
libdvdread: Elapsed time 0
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
libdvdread: Get key for /VIDEO_TS/VTS_24_1.VOB at 0x003d47a9
libdvdread: Elapsed time 0
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
libdvdread: Get key for /VIDEO_TS/VTS_25_0.VOB at 0x003d4e94
libdvdread: Elapsed time 0
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
libdvdread: Get key for /VIDEO_TS/VTS_25_1.VOB at 0x003d4ee1
libdvdread: Elapsed time 0
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
libdvdread: Get key for /VIDEO_TS/VTS_26_0.VOB at 0x003d551b
libdvdread: Elapsed time 0
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
libdvdread: Get key for /VIDEO_TS/VTS_26_1.VOB at 0x003d5568
libdvdread: Elapsed time 0
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
libdvdread: Get key for /VIDEO_TS/VTS_27_0.VOB at 0x003d5b8d
libdvdread: Elapsed time 0
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
libdvdread: Get key for /VIDEO_TS/VTS_27_1.VOB at 0x003d5bda
libdvdread: Elapsed time 0
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
libdvdread: Get key for /VIDEO_TS/VTS_28_0.VOB at 0x003d6236
libdvdread: Elapsed time 0
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
libdvdread: Get key for /VIDEO_TS/VTS_28_1.VOB at 0x003d6283
libdvdread: Elapsed time 0
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
libdvdread: Get key for /VIDEO_TS/VTS_29_1.VOB at 0x003d6828
libdvdread: Elapsed time 0
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
libdvdread: Get key for /VIDEO_TS/VTS_30_1.VOB at 0x003d6889
libdvdread: Elapsed time 0
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
libdvdread: Get key for /VIDEO_TS/VTS_31_1.VOB at 0x003d9efb
libdvdread: Elapsed time 0
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
libdvdread: Get key for /VIDEO_TS/VTS_32_1.VOB at 0x003dba88
libdvdread: Elapsed time 0
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
libdvdread: Get key for /VIDEO_TS/VTS_33_1.VOB at 0x003ea185
libdvdread: Elapsed time 0
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
libdvdread: Get key for /VIDEO_TS/VTS_34_1.VOB at 0x003ebf9e
libdvdread: Elapsed time 0
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
libdvdread: Found 34 VTS's
libdvdread: Elapsed time 4
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
[00000343] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
[00000383] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000
libdvdnav: Could not locate block
libdvdnav: Error when seeking
libdvdnav: FIXME: Implement seeking to location 14520
[00000292] main input error: INPUT_CONTROL_SET_POSITION(_OFFSET) 100.0% failed
libdvdnav: Could not locate block
libdvdnav: Error when seeking
libdvdnav: FIXME: Implement seeking to location 14524
[00000292] main input error: INPUT_CONTROL_SET_POSITION(_OFFSET) 100.0% failed
libdvdnav: Error when seeking
libdvdnav: FIXME: Implement seeking to location 0
[00000292] main input error: INPUT_CONTROL_SET_POSITION(_OFFSET) 100.0% failed
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
libdvdnav: Suspected RCE Region Protection!!!
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
[00000391] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
[00000400] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:384000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
[00000410] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:384000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
*** Zero check failed in ifo_read.c:327
    for vmgi_mat->zero_6 = 0x0000001600000000000000000000000000000000000000000000000000000000
[00000418] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:384000
```

Either way, I get no sound, any ideas?

---

### Post by asenine on 2008-08-29
leo_away requested the output if I were to play an mp3. I don't know if this will help or not, but here it is:

```
mdb:511, lastbuf:0 skiping granule 0
mdb:511, lastbuf:0 skiping granule 0
mdb:511, lastbuf:0 skiping granule 1
mdb:511, lastbuf:0 skiping granule 1
invalid new backstep 591
mdb:511, lastbuf:0 skiping granule 0
mdb:511, lastbuf:0 skiping granule 0
mdb:511, lastbuf:0 skiping granule 1
mdb:511, lastbuf:0 skiping granule 1
invalid new backstep 591
invalid new backstep 591
invalid new backstep 591
invalid new backstep 591
invalid new backstep 591
invalid new backstep 591
invalid new backstep 591
invalid new backstep 591
invalid new backstep 513
invalid new backstep 520
invalid new backstep 513
invalid new backstep 513
invalid new backstep 518
invalid new backstep 514
invalid new backstep 518

```

---

### Post by Crafty Kisses on 2008-08-30
Post the results of > lspci -v

---

### Post by quanumphaze on 2008-08-30
This could be a VLC vs PulseAudio problem since other programs still work with sound. I recommend you check out some of the PulseAudio fix threads in the Tutorials & Tips section first. VLC always worked with audio for me but it was always making crackles and skipping.

You can try to set VLC to use OSS instead of Alsa or Pulse.
Go into the VLC prefs, tick advanced options in the corner and "Audio>Output modules" and set the menubox to OSS. Close VLC and run it using "padsp vlc" from a terminal to see if it works. If it does than you can edit the menu entry to use "padsp vlc".
"padsp" is a OSS->PulseAudio wrapper

---

### Post by asenine on 2008-08-30
> **Codename said:**
> Post the results of > lspci -v
```
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
	Subsystem: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: f8000000-fbffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>

00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 502c
	Flags: bus master, fast devsel, latency 0, IRQ 221
	Memory at fdfc0000 (32-bit, non-prefetchable) [size=128K]
	Memory at fdfff000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at ff00 [size=32]
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7502
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at fe00 [size=32]
	Capabilities: <access denied>

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7502
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at fd00 [size=32]
	Capabilities: <access denied>

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7502
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at fc00 [size=32]
	Capabilities: <access denied>

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7502
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at fdffe000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7502
	Flags: bus master, fast devsel, latency 0, IRQ 23
	Memory at fdff4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7502
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at fb00 [size=32]
	Capabilities: <access denied>

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7502
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at fa00 [size=32]
	Capabilities: <access denied>

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7502
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at f900 [size=32]
	Capabilities: <access denied>

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7502
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at fdffd000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fdd00000-fddfffff
	Prefetchable memory behind bridge: 00000000fde00000-00000000fdefffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801IH (ICH9DH) LPC Interface Controller (rev 02)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7502
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.2 SATA controller: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7502
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 222
	I/O ports at f800 [size=8]
	I/O ports at f700 [size=4]
	I/O ports at f600 [size=8]
	I/O ports at f500 [size=4]
	I/O ports at f400 [size=32]
	Memory at fdffc000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7502
	Flags: medium devsel, IRQ 11
	Memory at fdffb000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 0500 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GS (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 0963
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at f8000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at df00 [size=128]
	[virtual] Expansion ROM at fb000000 [disabled] [size=128K]
	Capabilities: <access denied>

02:01.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
	Subsystem: Creatix Polymedia GmbH Unknown device 000d
	Flags: bus master, medium devsel, latency 84, IRQ 22
	Memory at fddff000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

02:02.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0) (prog-if 10 [OHCI])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 502d
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at fddfe000 (32-bit, non-prefetchable) [size=2K]
	I/O ports at cf00 [size=128]
	Capabilities: <access denied>

```

> **quanumphaze said:**
> I recommend you check out some of the PulseAudio fix threads in the Tutorials & Tips section first.
Okay, will do.

> **quanumphaze said:**
> You can try to set VLC to use OSS instead of Alsa or Pulse. 
Go into the VLC prefs, tick advanced options in the corner and "Audio>Output modules" and set the menubox to OSS. Close VLC and run it using "padsp vlc" from a terminal to see if it works. If it does than you can edit the menu entry to use "padsp vlc".
"padsp" is a OSS->PulseAudio wrapper
I get no sound when I do that.

---

