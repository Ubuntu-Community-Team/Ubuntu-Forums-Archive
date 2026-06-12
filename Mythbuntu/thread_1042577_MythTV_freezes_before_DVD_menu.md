---
title: "MythTV freezes before DVD menu"
date: 2009-01-17
forum: Mythbuntu
---

### Post by Cheeseroue on 2009-01-17
MythTV freezes during DVD playback, particularly just before opening the DVD menu. and I end up having to kill it from task manager. DVD's play fine in VLC and Kaffine however. This is in Hardy Mythbuntu and 0.21 MythTV.

Here is the frontend log showing the stalled DVD playback. I'd really appreciate some help translating this-this is still quite over my head.

> 2009-01-17 17:40:58.754 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-01-17 17:40:58.766 Using protocol version 40
2009-01-17 17:40:58.802 TV: Attempting to change from None to WatchingPreRecorded
libdvdread: Using libdvdcss version 1.2.9 for DVD access

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000015c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001aa
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000001e3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00004647
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00004680
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x0000f6e4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0001893d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x000189c4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x000189fd
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x0006ef8f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x0006efc8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x000c39e8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x000c3a21
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x0011839c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x001183d5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x0016cb91
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x0016cbca
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x001c030f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x001c0348
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x00212e1d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x00212e56
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_0.VOB at 0x00267595
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x002675ce
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_0.VOB at 0x002bbee2
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_1.VOB at 0x002bbf1b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_0.VOB at 0x00313720
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_1.VOB at 0x00313759
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_0.VOB at 0x00368274
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_1.VOB at 0x003682ad
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_0.VOB at 0x00368b13
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_1.VOB at 0x00368b4c
libdvdread: Elapsed time 0
libdvdread: Found 15 VTS's
libdvdread: Elapsed time 0
libdvdnav: Using dvdnav version 0.1.10-xine from [http://xine.sf.net](http://xine.sf.net)
libdvdnav: DVD Title: 30ROCK_SEASON_2_DISC_1
libdvdnav: DVD Serial Number: 38E782AEAPPLEDSP
libdvdnav: DVD Title (Alternative): 30ROCK_SEASON_2_DISC_1
libdvdnav: Unable to find map file '/home/arthur/.dvdnav/30ROCK SEASON 2 DISC 1.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
2009-01-17 17:41:01.917 Opened DVD device at /dev/dvd
2009-01-17 17:41:01.918 There are 15 titles on the disk
2009-01-17 17:41:01.918 Title 0 has 0 parts.
2009-01-17 17:41:01.918 Title 1 has 4 parts.
2009-01-17 17:41:01.918 Title 2 has 6 parts.
2009-01-17 17:41:01.918 Title 3 has 1 parts.
2009-01-17 17:41:01.919 Title 4 has 2 parts.
2009-01-17 17:41:01.919 Title 5 has 2 parts.
2009-01-17 17:41:01.919 Title 6 has 2 parts.
2009-01-17 17:41:01.919 Title 7 has 2 parts.
2009-01-17 17:41:01.919 Title 8 has 2 parts.
2009-01-17 17:41:01.920 Title 9 has 2 parts.
2009-01-17 17:41:01.920 Title 10 has 2 parts.
2009-01-17 17:41:01.920 Title 11 has 2 parts.
2009-01-17 17:41:01.920 Title 12 has 2 parts.
2009-01-17 17:41:01.920 Title 13 has 2 parts.
2009-01-17 17:41:01.920 Title 14 has 1 parts.
2009-01-17 17:41:02.040 DPMS Deactivated 
2009-01-17 17:41:02.223 AFD: Opened codec 0x864c1f0, id(MPEG2VIDEO) type(Video)
2009-01-17 17:41:02.245 AFD: Opened codec 0x864c560, id(DVD_SUBTITLE) type(Subtitle)
2009-01-17 17:41:02.245 NVP: Disabling Audio, params(-1,-1,-1)
2009-01-17 17:41:02.472 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-01-17 17:41:02.656 OSD Theme Dimensions W: 640 H: 480
2009-01-17 17:41:04.393 TV: Changing from None to WatchingPreRecorded
2009-01-17 17:41:04.455 AFD: Warning, video codec 0x864c1f0 id(MPEG2VIDEO) type (Video) already open.
2009-01-17 17:41:04.455 AFD: Opened codec 0x9492180, id(DVD_SUBTITLE) type(Subtitle)
2009-01-17 17:41:04.602 Video timing method: USleep with busy wait
2009-01-17 17:41:05.005 AFD: Warning, video codec 0x864c1f0 id(MPEG2VIDEO) type (Video) already open.
2009-01-17 17:41:05.402 AFD: codec AC3 has 0 channels
2009-01-17 17:41:05.437 AFD: Opened codec 0x9496fb0, id(AC3) type(Audio)
2009-01-17 17:41:05.473 Opening audio device 'default'. ch 2(2) sr 48000
2009-01-17 17:41:05.473 Opening ALSA audio device 'default'.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL /dev/mixer
2009-01-17 17:41:05.595 AudioOutput Warning: Mixer attach error -2: No such file or directory
            Check Mixer Name in Setup: '/dev/mixer'
2009-01-17 17:41:05.597 NVP: Enabling Audio
2009-01-17 17:41:05.641 AFD: Warning, video codec 0x864c1f0 id(MPEG2VIDEO) type (Video) already open.
2009-01-17 17:41:05.644 AFD: Warning, audio codec 0x9496fb0 id(AC3) type (Audio) already open, leaving it alone.
2009-01-17 17:41:05.644 AFD: codec AC3 has 2 channels
2009-01-17 17:41:05.644 AFD: codec AC3 has 0 channels
2009-01-17 17:41:05.647 AFD: Opened codec 0x8ae3e80, id(AC3) type(Audio)
2009-01-17 17:41:05.666 AFD: Warning, video codec 0x864c1f0 id(MPEG2VIDEO) type (Video) already open.
2009-01-17 17:41:05.666 AFD: Warning, audio codec 0x9496fb0 id(AC3) type (Audio) already open, leaving it alone.
2009-01-17 17:41:05.666 AFD: codec AC3 has 2 channels
2009-01-17 17:41:05.666 AFD: Warning, audio codec 0x8ae3e80 id(AC3) type (Audio) already open, leaving it alone.
2009-01-17 17:41:05.667 AFD: codec AC3 has 2 channels
2009-01-17 17:41:05.667 AFD: codec AC3 has 0 channels
2009-01-17 17:41:05.668 AFD: Opened codec 0x8aec540, id(AC3) type(Audio)
2009-01-17 17:41:05.671 AFD: Warning, audio codec 0x9496fb0 id(AC3) type (Audio) already open, leaving it alone.
2009-01-17 17:41:05.671 AFD: codec AC3 has 2 channels
2009-01-17 17:41:05.671 AFD: Warning, audio codec 0x8ae3e80 id(AC3) type (Audio) already open, leaving it alone.
2009-01-17 17:41:05.671 AFD: codec AC3 has 2 channels
2009-01-17 17:41:05.671 AFD: Warning, audio codec 0x8aec540 id(AC3) type (Audio) already open, leaving it alone.
2009-01-17 17:41:05.671 AFD: codec AC3 has 2 channels
2009-01-17 17:41:05.933 NVP: Prebuffer wait timed out 10 times.
2009-01-17 17:41:26.746 DPMS Reactivated.
2009-01-17 17:41:27.659 DPMS Deactivated 
2009-01-17 17:41:27.659 DPMS Reactivated.
2009-01-17 17:41:41.736 DPMS Deactivated 
2009-01-17 17:41:51.489 DPMS Reactivated.
2009-01-17 17:41:52.515 [mpeg2video @ 0xb738ea88]ac-tex damaged at 28 1
2009-01-17 17:41:52.515 [mpeg2video @ 0xb738ea88]Warning MVs not available
2009-01-17 17:41:52.538 WriteAudio: buffer underrun
2009-01-17 17:41:52.580 [ac3 @ 0xb738ea88]frame CRC mismatch
2009-01-17 17:41:52.593 DPMS Deactivated 
2009-01-17 17:41:52.594 DPMS Reactivated.
2009-01-17 17:45:13.468 WriteAudio: buffer underrun


2009-01-17 17:45:45.951 TV: Attempting to change from WatchingPreRecorded to NoneThanks!

(edited to fix smiley)

---

### Post by Dewey_Oxberger on 2009-04-26
I'm having the same problem.  It's occuring at the copyright or fbi warning.  Player just freezes.  My logs look totally different.  The only problem I see in common is the AC3 frame CRC error just before the freeze.

Any word on when 0.22 will be out?

---

