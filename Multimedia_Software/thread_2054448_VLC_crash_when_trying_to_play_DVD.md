---
title: "VLC crash when trying to play DVD"
date: 2012-09-07
forum: Multimedia Software
---

### Post by sssSami on 2012-09-07
Hey! When I try to play the DVD "Underworld Evolution", VLC just suddenly crash. The previous DVD, simply called "Underworld" worked just fine yesterday.

Here's what the Terminal returned when I entered "vlc /dev/dvd":
```
VLC media player 2.0.3 Twoflower (revision 2.0.2-93-g77aa89e)
[0x8d1b908] main libvlc: Kjører VLC med standardbrukerflaten. Bruk «cvlc» for å kjøre VLC uten en brukerflate.
"sni-qt/4919" WARN  15:30:40.981 void StatusNotifierItemFactory::connectToSnw() Invalid interface to SNW_SERVICE 
libdvdnav: Using dvdnav version 4.2.0
libdvdread: Using libdvdcss version 1.2.12 for DVD access
libdvdnav: DVD Title: UNDERWORLD_EVOLUTION
libdvdnav: DVD Serial Number: 4464CBA1___MVB__
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/sami/.dvdnav/UNDERWORLD_EVOLUTION.map'
libdvdnav: DVD disk reports itself with Region mask 0x00ed0000. Regions: 2 5

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x000001c1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00005054
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00022c60
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00288ce6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00288d33
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00290900
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0029094d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x00297d87
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x00297dd4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x002a01ab
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x002a01f8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x002a54fd
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x002a554a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x002aecb1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x002aecfe
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x002b8403
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x002b8450
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x002ec795
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x002ec7e2
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x0031efa1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x0031efee
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_0.VOB at 0x0034d4ff
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x0034d54c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_0.VOB at 0x00373bea
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_1.VOB at 0x00373c37
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_0.VOB at 0x003a5fa3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_1.VOB at 0x003a5ff0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_0.VOB at 0x003d3ed1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_1.VOB at 0x003d3f1e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_0.VOB at 0x003e4cc5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_1.VOB at 0x003e4d12
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_16_0.VOB at 0x003e60e4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_16_1.VOB at 0x003e6131
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_17_0.VOB at 0x003e9a01
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_17_1.VOB at 0x003e9a4e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_18_0.VOB at 0x003ea9e9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_18_1.VOB at 0x003eaa36
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_19_0.VOB at 0x003eba17
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_19_1.VOB at 0x003eba64
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_20_0.VOB at 0x003ee9cd
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_20_1.VOB at 0x003eea1a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_21_0.VOB at 0x003eeb65
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_21_1.VOB at 0x003eebb2
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_22_0.VOB at 0x003ef19e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_22_1.VOB at 0x003ef1eb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_23_0.VOB at 0x003ef8c5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_23_1.VOB at 0x003ef912
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_24_0.VOB at 0x003efff1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_24_1.VOB at 0x003f003e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_25_0.VOB at 0x003f0642
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_25_1.VOB at 0x003f068f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_26_0.VOB at 0x003f0b0f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_26_1.VOB at 0x003f0b5c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_27_0.VOB at 0x003f101e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_27_1.VOB at 0x003f106b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_28_0.VOB at 0x003f15f7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_28_1.VOB at 0x003f1644
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_29_0.VOB at 0x003f19fa
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_29_1.VOB at 0x003f1a47
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_30_0.VOB at 0x003f1ecd
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_30_1.VOB at 0x003f1f1a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_31_0.VOB at 0x003f255c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_31_1.VOB at 0x003f25a9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_32_0.VOB at 0x003f2a6d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_32_1.VOB at 0x003f2aba
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_33_0.VOB at 0x003f2c95
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_33_1.VOB at 0x003f2dad
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_34_0.VOB at 0x003f9f9e
libdvdread: Elapsed time 0
libdvdread: Found 33 VTS's
libdvdread: Elapsed time 0

*** libdvdread: CHECK_VALUE failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:843 ***
*** for cell_playback[i].first_sector <= cell_playback[i].last_vobu_start_sector ***


*** libdvdread: CHECK_VALUE failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:843 ***
*** for cell_playback[i].first_sector <= cell_playback[i].last_vobu_start_sector ***


*** libdvdread: CHECK_VALUE failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:843 ***
*** for cell_playback[i].first_sector <= cell_playback[i].last_vobu_start_sector ***


*** libdvdread: CHECK_VALUE failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:843 ***
*** for cell_playback[i].first_sector <= cell_playback[i].last_vobu_start_sector ***

*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04

*** libdvdread: CHECK_VALUE failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:843 ***
*** for cell_playback[i].first_sector <= cell_playback[i].last_vobu_start_sector ***


*** libdvdread: CHECK_VALUE failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:843 ***
*** for cell_playback[i].first_sector <= cell_playback[i].last_vobu_start_sector ***


*** libdvdread: CHECK_VALUE failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:843 ***
*** for cell_playback[i].first_sector <= cell_playback[i].last_vobu_start_sector ***


*** libdvdread: CHECK_VALUE failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:843 ***
*** for cell_playback[i].first_sector <= cell_playback[i].last_vobu_start_sector ***

*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:864
    for cell_position[i].zero_1 = 0x04
Minnesegmentsfeil (core dumped)

```

The DVD's surface is clean.
Is there anything I can do to make VLC(or another player) simply play the DVD, rather than crash?
Hope I get a quick answer, since I'd like to see the movie without having to use my desktop, wich currently doesn't even have it's cables(monitor, power, mouse, keyboard etc) connected.

---

### Post by sssSami on 2012-09-07
MPlayer, like before, didn't work. Altough Totem seems to work, since it got to the DVD menu.

I guess I solved it myself B-)

Edit: Laggy as hell

---

