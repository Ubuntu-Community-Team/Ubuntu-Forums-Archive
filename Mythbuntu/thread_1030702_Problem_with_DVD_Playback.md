---
title: "Problem with DVD Playback"
date: 2009-01-04
forum: Mythbuntu
---

### Post by murbanci on 2009-01-04
Ive been trying to play my DVDs using the internal player and when I do, the picture is very pixelated, only for the actual movie, however, the menu and special features play fine.  This makes me think it has something to do with decoding he DVD but I have no idea where to go from here.  Any help would be appreciated. 

Here is the output of the log file:
```

==> /var/log/mythtv/mythfrontend.log <==
2009-01-04 17:04:09.973 [mpeg2video @ 0xb72e9764]ac-tex damaged at 31 14
2009-01-04 17:04:09.974 [mpeg2video @ 0xb72e9764]mb incr damaged
2009-01-04 17:04:09.977 [ac3 @ 0xb72e9764]frame CRC mismatch
2009-01-04 17:04:09.978 [ac3 @ 0xb72e9764]frame CRC mismatch
2009-01-04 17:04:09.979 [mpeg2video @ 0xb72e9764]ac-tex damaged at 35 3
2009-01-04 17:04:09.979 [mpeg2video @ 0xb72e9764]mb incr damaged
2009-01-04 17:04:09.979 [mpeg2video @ 0xb72e9764]ac-tex damaged at 36 8
2009-01-04 17:04:09.980 [mpeg2video @ 0xb72e9764]ac-tex damaged at 40 10
2009-01-04 17:04:09.980 [mpeg2video @ 0xb72e9764]ac-tex damaged at 27 12
2009-01-04 17:04:09.980 [mpeg2video @ 0xb72e9764]ac-tex damaged at 8 15
2009-01-04 17:04:09.980 [mpeg2video @ 0xb72e9764]invalid cbp at 22 17
2009-01-04 17:04:09.981 [mpeg2video @ 0xb72e9764]ac-tex damaged at 3 22
2009-01-04 17:04:09.981 [mpeg2video @ 0xb72e9764]ac-tex damaged at 15 24
2009-01-04 17:04:09.998 [mpeg2video @ 0xb72e9764]ac-tex damaged at 10 3
2009-01-04 17:04:09.999 [mpeg2video @ 0xb72e9764]ac-tex damaged at 21 8
2009-01-04 17:04:09.999 [mpeg2video @ 0xb72e9764]mb incr damaged
2009-01-04 17:04:10.000 [mpeg2video @ 0xb72e9764]ac-tex damaged at 24 23
2009-01-04 17:04:10.000 [mpeg2video @ 0xb72e9764]invalid mb type in B Frame at 21 3
2009-01-04 17:04:10.000 [mpeg2video @ 0xb72e9764]slice mismatch
2009-01-04 17:04:10.000 [mpeg2video @ 0xb72e9764]mb incr damaged
2009-01-04 17:04:10.000 [mpeg2video @ 0xb72e9764]ac-tex damaged at 7 9
2009-01-04 17:04:10.000 [mpeg2video @ 0xb72e9764]ac-tex damaged at 31 13
2009-01-04 17:04:10.000 [mpeg2video @ 0xb72e9764]ac-tex damaged at 6 16
2009-01-04 17:04:10.000 [mpeg2video @ 0xb72e9764]invalid cbp at 41 15
2009-01-04 17:04:10.001 [mpeg2video @ 0xb72e9764]invalid cbp at 20 20
2009-01-04 17:04:10.001 [mpeg2video @ 0xb72e9764]invalid mb type in B Frame at 15 21
2009-01-04 17:04:10.001 [mpeg2video @ 0xb72e9764]slice mismatch
2009-01-04 17:04:10.001 [mpeg2video @ 0xb72e9764]slice mismatch
2009-01-04 17:04:10.001 [mpeg2video @ 0xb72e9764]ac-tex damaged at 35 24
2009-01-04 17:04:10.001 [mpeg2video @ 0xb72e9764]ac-tex damaged at 0 4
2009-01-04 17:04:10.001 [mpeg2video @ 0xb72e9764]slice mismatch
2009-01-04 17:04:10.001 [mpeg2video @ 0xb72e9764]invalid cbp at 1 8
2009-01-04 17:04:10.001 [mpeg2video @ 0xb72e9764]slice mismatch
2009-01-04 17:04:10.001 [mpeg2video @ 0xb72e9764]invalid cbp at 1 11
2009-01-04 17:04:10.001 [mpeg2video @ 0xb72e9764]invalid mb type in B Frame at 39 13
2009-01-04 17:04:10.002 [mpeg2video @ 0xb72e9764]invalid cbp at 13 15
2009-01-04 17:04:10.002 [mpeg2video @ 0xb72e9764]invalid mb type in B Frame at 8 18
2009-01-04 17:04:10.002 [mpeg2video @ 0xb72e9764]slice mismatch
2009-01-04 17:04:10.002 [mpeg2video @ 0xb72e9764]mb incr damaged
2009-01-04 17:04:10.002 [mpeg2video @ 0xb72e9764]mb incr damaged
2009-01-04 17:04:10.002 [mpeg2video @ 0xb72e9764]slice mismatch
2009-01-04 17:04:10.002 [mpeg2video @ 0xb72e9764]mb incr damaged
2009-01-04 17:04:10.027 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-04 17:04:10.028 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-04 17:04:10.053 [ac3 @ 0xb72e9764]frame CRC mismatch
2009-01-04 17:04:10.057 [ac3 @ 0xb72e9764]frame CRC mismatch
2009-01-04 17:04:10.058 [mpeg2video @ 0xb72e9764]sequence header damaged
2009-01-04 17:04:10.058 [mpeg2video @ 0xb72e9764]invalid cbp at 17 7
2009-01-04 17:04:10.058 [mpeg2video @ 0xb72e9764]ac-tex damaged at 10 14
2009-01-04 17:04:10.058 [mpeg2video @ 0xb72e9764]ac-tex damaged at 10 17
2009-01-04 17:04:10.058 [mpeg2video @ 0xb72e9764]ac-tex damaged at 10 18
2009-01-04 17:04:10.058 [mpeg2video @ 0xb72e9764]slice mismatch
2009-01-04 17:04:10.058 [mpeg2video @ 0xb72e9764]ac-tex damaged at 10 24
2009-01-04 17:04:10.058 [mpeg2video @ 0xb72e9764]ac-tex damaged at 10 27
2009-01-04 17:04:10.059 [mpeg2video @ 0xb72e9764]ac-tex damaged at 10 28
2009-01-04 17:04:10.059 [mpeg2video @ 0xb72e9764]ac-tex damaged at 10 29
2009-01-04 17:04:10.062 [ac3 @ 0xb72e9764]frame CRC mismatch
2009-01-04 17:04:10.063 [ac3 @ 0xb72e9764]frame CRC mismatch
2009-01-04 17:04:10.063 GetNextFreeFrame() served a busy frame F. Dropping. UUUUUUUUUUUUUUUUUUUUUUUUUUUULuU
2009-01-04 17:04:10.064 [mpeg2video @ 0xb72e9764]ac-tex damaged at 41 10
2009-01-04 17:04:10.065 [mpeg2video @ 0xb72e9764]invalid mb type in B Frame at 26 20
2009-01-04 17:04:10.112 [mpeg2video @ 0xb72e9764]ac-tex damaged at 4 6
2009-01-04 17:04:10.112 [mpeg2video @ 0xb72e9764]slice mismatch
2009-01-04 17:04:10.113 [mpeg2video @ 0xb72e9764]mb incr damaged
2009-01-04 17:04:10.113 [mpeg2video @ 0xb72e9764]invalid mb type in B Frame at 4 25
2009-01-04 17:04:10.113 [mpeg2video @ 0xb72e9764]slice mismatch
2009-01-04 17:04:10.113 [mpeg2video @ 0xb72e9764]ac-tex damaged at 15 5
2009-01-04 17:04:10.113 [mpeg2video @ 0xb72e9764]invalid cbp at 10 7
2009-01-04 17:04:10.114 [mpeg2video @ 0xb72e9764]ac-tex damaged at 12 9
2009-01-04 17:04:10.114 [mpeg2video @ 0xb72e9764]ac-tex damaged at 10 9
2009-01-04 17:04:10.114 [mpeg2video @ 0xb72e9764]invalid mb type in B Frame at 26 13
2009-01-04 17:04:10.114 [mpeg2video @ 0xb72e9764]ac-tex damaged at 32 14
2009-01-04 17:04:10.114 [mpeg2video @ 0xb72e9764]mb incr damaged
2009-01-04 17:04:10.114 [mpeg2video @ 0xb72e9764]ac-tex damaged at 0 18
2009-01-04 17:04:10.114 [mpeg2video @ 0xb72e9764]slice mismatch
2009-01-04 17:04:10.114 [mpeg2video @ 0xb72e9764]ac-tex damaged at 10 22
2009-01-04 17:04:10.114 [mpeg2video @ 0xb72e9764]ac-tex damaged at 8 23
2009-01-04 17:04:10.114 [mpeg2video @ 0xb72e9764]mb incr damaged
2009-01-04 17:04:10.114 [mpeg2video @ 0xb72e9764]slice mismatch
2009-01-04 17:04:10.115 [mpeg2video @ 0xb72e9764]invalid mb type in B Frame at 10 9
2009-01-04 17:04:10.115 [mpeg2video @ 0xb72e9764]ac-tex damaged at 10 10
2009-01-04 17:04:10.115 [mpeg2video @ 0xb72e9764]invalid cbp at 25 11
2009-01-04 17:04:10.115 [mpeg2video @ 0xb72e9764]invalid mb type in B Frame at 9 12
2009-01-04 17:04:10.115 [mpeg2video @ 0xb72e9764]ac-tex damaged at 7 18
2009-01-04 17:04:10.115 [mpeg2video @ 0xb72e9764]invalid mb type in B Frame at 18 19
2009-01-04 17:04:10.115 [mpeg2video @ 0xb72e9764]invalid mb type in B Frame at 11 20
2009-01-04 17:04:10.115 [mpeg2video @ 0xb72e9764]invalid cbp at 40 21
2009-01-04 17:04:10.115 [mpeg2video @ 0xb72e9764]ac-tex damaged at 14 4
2009-01-04 17:04:10.116 [mpeg2video @ 0xb72e9764]slice mismatch
2009-01-04 17:04:10.116 [mpeg2video @ 0xb72e9764]ac-tex damaged at 40 21
2009-01-04 17:04:10.161 [ac3 @ 0xb72e9764]frame CRC mismatch
2009-01-04 17:04:10.162 [mpeg2video @ 0xb72e9764]invalid mb type in P Frame at 23 4
2009-01-04 17:04:10.162 [mpeg2video @ 0xb72e9764]invalid mb type in P Frame at 0 9
2009-01-04 17:04:10.163 [mpeg2video @ 0xb72e9764]ac-tex damaged at 28 15
2009-01-04 17:04:10.163 [mpeg2video @ 0xb72e9764]ac-tex damaged at 41 20
2009-01-04 17:04:10.244 [mpeg2video @ 0xb72e9764]ac-tex damaged at 19 4
2009-01-04 17:04:10.246 [mpeg2video @ 0xb72e9764]invalid mb type in B Frame at 1 19
2009-01-04 17:04:10.281 TV: Attempting to change from WatchingPreRecorded to None
2009-01-04 17:04:10.323 TV: Changing from WatchingPreRecorded to None
2009-01-04 17:04:13.748 Deleting UPnP client...


```

---

### Post by newlinux on 2009-01-04
can you give the log from the beginning of playback? Do you have problems with the internal player with other file types?

---

### Post by murbanci on 2009-01-04
It plays avi, mkv, and vob (from ripped dvds) fine.  I havent tested any other file types.

The first time I tried to play it MythTV crashed and this was the output of the log:
```

==> /var/log/mythtv/mythfrontend.log <==
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0004b0b3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x002335c0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x002335e0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x002d4d00
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002d4d20
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x002d8920
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x002d8940
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x002f4800
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x002f4820
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x002f5de0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x002f5e00
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x002ff520
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x002ff540
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x00309c00
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x00309c20
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x0030ffa0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x0030ffc0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_09_1.VOB (0x0030ffc0)!!
libdvdread: Elapsed time 17
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x0031a280
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x0031a2a0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_10_1.VOB (0x0031a2a0)!!
libdvdread: Elapsed time 5
libdvdread: Get key for /VIDEO_TS/VTS_11_0.VOB at 0x0031f6e0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_11_0.VOB (0x0031f6e0)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x0031f7a0
libdvdread: Elapsed time 0
libdvdread: Found 11 VTS's
libdvdread: Elapsed time 23
libdvdnav: Using dvdnav version 0.1.10-xine from http://xine.sf.net
libdvdnav: DVD Title: DVD_VIDEO
libdvdnav: DVD Serial Number: 2D338477
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/murbancic/.dvdnav/DVD VIDEO.map'
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8
2009-01-04 19:15:37.932 Opened DVD device at /dev/dvd1
libdvdnav: Suspected RCE Region Protection!!!
2009-01-04 19:15:37.940 There are 24 titles on the disk
2009-01-04 19:15:37.940 Title 0 has 0 parts.
2009-01-04 19:15:37.940 Title 1 has 28 parts.
2009-01-04 19:15:37.941 Title 2 has 2 parts.
2009-01-04 19:15:37.941 Title 3 has 2 parts.
2009-01-04 19:15:37.941 Title 4 has 2 parts.
2009-01-04 19:15:37.941 Title 5 has 2 parts.
2009-01-04 19:15:37.941 Title 6 has 2 parts.
2009-01-04 19:15:37.941 Title 7 has 2 parts.
2009-01-04 19:15:37.941 Title 8 has 2 parts.
2009-01-04 19:15:37.941 Title 9 has 2 parts.
2009-01-04 19:15:37.941 Title 10 has 2 parts.
2009-01-04 19:15:37.941 Title 11 has 2 parts.
2009-01-04 19:15:37.941 Title 12 has 2 parts.
2009-01-04 19:15:37.941 Title 13 has 2 parts.
2009-01-04 19:15:37.941 Title 14 has 2 parts.
2009-01-04 19:15:37.941 Title 15 has 2 parts.
2009-01-04 19:15:37.941 Title 16 has 2 parts.
2009-01-04 19:15:37.941 Title 17 has 2 parts.
2009-01-04 19:15:37.941 Title 18 has 2 parts.
2009-01-04 19:15:37.941 Title 19 has 2 parts.
2009-01-04 19:15:37.941 Title 20 has 2 parts.
2009-01-04 19:15:37.942 Title 21 has 2 parts.
2009-01-04 19:15:37.942 Title 22 has 2 parts.
2009-01-04 19:15:37.942 Title 23 has 2 parts.
2009-01-04 19:15:38.025 DPMS Deactivated 
2009-01-04 19:15:38.288 AFD: Opened codec 0xa4abac0, id(MPEG2VIDEO) type(Video)
2009-01-04 19:15:38.288 NVP: Disabling Audio, params(-1,-1,-1)
2009-01-04 19:15:38.381 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-01-04 19:15:38.506 OSD Theme Dimensions W: 640 H: 480
2009-01-04 19:15:39.034 TV: Changing from None to WatchingPreRecorded
2009-01-04 19:15:39.192 Video timing method: USleep with busy wait
2009-01-04 19:15:39.221 AFD: Warning, video codec 0xa4abac0 id(MPEG2VIDEO) type (Video) already open.
2009-01-04 19:15:39.352 AFD: codec AC3 has 0 channels
2009-01-04 19:15:39.374 AFD: Opened codec 0xb0370b0, id(AC3) type(Audio)
2009-01-04 19:15:39.390 Opening audio device 'default'. ch 2(2) sr 48000
2009-01-04 19:15:39.390 Opening ALSA audio device 'default'.
2009-01-04 19:15:39.498 mixer unable to find control Master 1
2009-01-04 19:15:39.499 NVP: Enabling Audio
2009-01-04 19:15:39.499 AFD: Warning, audio codec 0xb0370b0 id(AC3) type (Audio) already open, leaving it alone.
2009-01-04 19:15:39.499 AFD: codec AC3 has 2 channels
libdvdnav: Suspected RCE Region Protection!!!
2009-01-04 19:16:13.201 AFD: Warning, video codec 0xa4abac0 id(MPEG2VIDEO) type (Video) already open.
2009-01-04 19:16:13.221 AFD: Opened codec 0xa85a64a0, id(DVD_SUBTITLE) type(Subtitle)
2009-01-04 19:16:13.221 NVP: Disabling Audio, params(-1,-1,-1)

```

Then I tried playing it again, with the same problem (pixelated picture) and this was the output of the log:
```

==> /var/log/mythtv/mythfrontend.log <==
2009-01-04 19:21:53.753 [mpeg2video @ 0xb72f2764]mb incr damaged
2009-01-04 19:21:53.753 [mpeg2video @ 0xb72f2764]ac-tex damaged at 10 17
2009-01-04 19:21:53.754 [mpeg2video @ 0xb72f2764]ac-tex damaged at 0 18
2009-01-04 19:21:53.754 [mpeg2video @ 0xb72f2764]invalid mb type in B Frame at 11 19
2009-01-04 19:21:53.754 [mpeg2video @ 0xb72f2764]mb incr damaged
2009-01-04 19:21:53.754 [mpeg2video @ 0xb72f2764]invalid cbp at 6 21
2009-01-04 19:21:53.754 [mpeg2video @ 0xb72f2764]ac-tex damaged at 23 22
2009-01-04 19:21:53.754 [mpeg2video @ 0xb72f2764]invalid cbp at 15 23
2009-01-04 19:21:53.754 [mpeg2video @ 0xb72f2764]slice mismatch
2009-01-04 19:21:53.754 [mpeg2video @ 0xb72f2764]mb incr damaged
2009-01-04 19:21:53.754 [mpeg2video @ 0xb72f2764]ac-tex damaged at 7 26
2009-01-04 19:21:53.754 [mpeg2video @ 0xb72f2764]invalid cbp at 27 27
2009-01-04 19:21:53.754 [mpeg2video @ 0xb72f2764]ac-tex damaged at 0 28
2009-01-04 19:21:53.754 [mpeg2video @ 0xb72f2764]ac-tex damaged at 0 29
2009-01-04 19:21:53.828 [ac3 @ 0xb72f2764]frame CRC mismatch
2009-01-04 19:21:53.870 [ac3 @ 0xb72f2764]frame CRC mismatch
2009-01-04 19:21:53.871 [mpeg2video @ 0xb72f2764]sequence header damaged
2009-01-04 19:21:53.871 [mpeg2video @ 0xb72f2764]ac-tex damaged at 10 4
2009-01-04 19:21:53.871 [mpeg2video @ 0xb72f2764]mb incr damaged
2009-01-04 19:21:53.871 [mpeg2video @ 0xb72f2764]ac-tex damaged at 10 21
2009-01-04 19:21:53.871 [mpeg2video @ 0xb72f2764]ac-tex damaged at 10 24
2009-01-04 19:21:53.871 [mpeg2video @ 0xb72f2764]ac-tex damaged at 10 26
2009-01-04 19:21:53.871 [mpeg2video @ 0xb72f2764]ac-tex damaged at 32 5
2009-01-04 19:21:53.872 [mpeg2video @ 0xb72f2764]mb incr damaged
2009-01-04 19:21:53.872 [mpeg2video @ 0xb72f2764]slice mismatch
2009-01-04 19:21:53.872 [mpeg2video @ 0xb72f2764]mb incr damaged
2009-01-04 19:21:53.872 [mpeg2video @ 0xb72f2764]mb incr damaged
2009-01-04 19:21:53.872 [mpeg2video @ 0xb72f2764]slice mismatch
2009-01-04 19:21:53.872 [mpeg2video @ 0xb72f2764]mb incr damaged
2009-01-04 19:21:53.872 [mpeg2video @ 0xb72f2764]mb incr damaged
2009-01-04 19:21:53.872 [mpeg2video @ 0xb72f2764]ac-tex damaged at 12 19
2009-01-04 19:21:53.872 [mpeg2video @ 0xb72f2764]mb incr damaged
2009-01-04 19:21:53.872 [mpeg2video @ 0xb72f2764]mb incr damaged
2009-01-04 19:21:53.873 [mpeg2video @ 0xb72f2764]invalid mb type in B Frame at 34 25
2009-01-04 19:21:53.873 [mpeg2video @ 0xb72f2764]ac-tex damaged at 30 26
2009-01-04 19:21:53.878 [mpeg2video @ 0xb72f2764]invalid mb type in B Frame at 11 3
2009-01-04 19:21:53.879 [mpeg2video @ 0xb72f2764]mb incr damaged
2009-01-04 19:21:53.879 [mpeg2video @ 0xb72f2764]ac-tex damaged at 19 15
2009-01-04 19:21:53.879 [mpeg2video @ 0xb72f2764]ac-tex damaged at 38 19
2009-01-04 19:21:53.880 [mpeg2video @ 0xb72f2764]ac-tex damaged at 17 22
2009-01-04 19:21:53.880 [mpeg2video @ 0xb72f2764]ac-tex damaged at 24 26
2009-01-04 19:21:53.880 [mpeg2video @ 0xb72f2764]slice mismatch
2009-01-04 19:21:53.880 [mpeg2video @ 0xb72f2764]invalid mb type in B Frame at 16 6
2009-01-04 19:21:53.880 [mpeg2video @ 0xb72f2764]ac-tex damaged at 0 8
2009-01-04 19:21:53.880 [mpeg2video @ 0xb72f2764]slice mismatch
2009-01-04 19:21:53.880 [mpeg2video @ 0xb72f2764]invalid cbp at 14 12
2009-01-04 19:21:53.880 [mpeg2video @ 0xb72f2764]invalid cbp at 1 14
2009-01-04 19:21:53.880 [mpeg2video @ 0xb72f2764]invalid mb type in B Frame at 8 16
2009-01-04 19:21:53.880 [mpeg2video @ 0xb72f2764]ac-tex damaged at 0 18
2009-01-04 19:21:53.881 [mpeg2video @ 0xb72f2764]slice mismatch
2009-01-04 19:21:53.881 [mpeg2video @ 0xb72f2764]ac-tex damaged at 1 22
2009-01-04 19:21:53.881 [mpeg2video @ 0xb72f2764]slice mismatch
2009-01-04 19:21:53.881 [mpeg2video @ 0xb72f2764]mb incr damaged
2009-01-04 19:21:53.881 [mpeg2video @ 0xb72f2764]ac-tex damaged at 19 6
2009-01-04 19:21:53.881 [mpeg2video @ 0xb72f2764]slice mismatch
2009-01-04 19:21:53.881 [mpeg2video @ 0xb72f2764]slice mismatch
2009-01-04 19:21:53.881 [mpeg2video @ 0xb72f2764]invalid cbp at 26 11
2009-01-04 19:21:53.881 [mpeg2video @ 0xb72f2764]ac-tex damaged at 30 12
2009-01-04 19:21:53.881 [mpeg2video @ 0xb72f2764]invalid cbp at 12 13
2009-01-04 19:21:53.881 [mpeg2video @ 0xb72f2764]invalid mb type in B Frame at 12 14
2009-01-04 19:21:53.881 [mpeg2video @ 0xb72f2764]slice mismatch
2009-01-04 19:21:53.882 [mpeg2video @ 0xb72f2764]slice mismatch
2009-01-04 19:21:53.882 [mpeg2video @ 0xb72f2764]mb incr damaged
2009-01-04 19:21:53.882 [mpeg2video @ 0xb72f2764]invalid mb type in B Frame at 24 21
2009-01-04 19:21:53.882 [mpeg2video @ 0xb72f2764]mb incr damaged
2009-01-04 19:21:53.882 [mpeg2video @ 0xb72f2764]ac-tex damaged at 26 24
2009-01-04 19:21:53.882 [mpeg2video @ 0xb72f2764]invalid mb type in B Frame at 34 6
2009-01-04 19:21:53.883 [mpeg2video @ 0xb72f2764]mb incr damaged
2009-01-04 19:21:53.883 [mpeg2video @ 0xb72f2764]ac-tex damaged at 23 15
2009-01-04 19:21:53.883 [mpeg2video @ 0xb72f2764]invalid mb type in B Frame at 20 19
2009-01-04 19:21:53.883 [mpeg2video @ 0xb72f2764]ac-tex damaged at 16 22
2009-01-04 19:21:53.884 [mpeg2video @ 0xb72f2764]ac-tex damaged at 1 27
2009-01-04 19:21:53.885 [mpeg2video @ 0xb72f2764]ac-tex damaged at 24 5
2009-01-04 19:21:53.885 [mpeg2video @ 0xb72f2764]ac-tex damaged at 3 6
2009-01-04 19:21:53.885 [mpeg2video @ 0xb72f2764]slice mismatch
2009-01-04 19:21:53.885 [mpeg2video @ 0xb72f2764]ac-tex damaged at 1 10
2009-01-04 19:21:53.885 [mpeg2video @ 0xb72f2764]ac-tex damaged at 9 12
2009-01-04 19:21:53.885 [mpeg2video @ 0xb72f2764]mb incr damaged
2009-01-04 19:21:53.885 [mpeg2video @ 0xb72f2764]ac-tex damaged at 1 14
2009-01-04 19:21:53.886 [mpeg2video @ 0xb72f2764]invalid cbp at 14 15
2009-01-04 19:21:53.886 [mpeg2video @ 0xb72f2764]invalid cbp at 14 16
2009-01-04 19:21:53.886 [mpeg2video @ 0xb72f2764]invalid cbp at 15 17
2009-01-04 19:21:53.886 [mpeg2video @ 0xb72f2764]mb incr damaged
2009-01-04 19:21:53.886 [mpeg2video @ 0xb72f2764]mb incr damaged
2009-01-04 19:21:53.886 [mpeg2video @ 0xb72f2764]ac-tex damaged at 2 20
2009-01-04 19:21:53.886 [mpeg2video @ 0xb72f2764]invalid cbp at 9 21
2009-01-04 19:21:53.886 [mpeg2video @ 0xb72f2764]slice mismatch
2009-01-04 19:21:53.886 [mpeg2video @ 0xb72f2764]mb incr damaged
2009-01-04 19:21:53.886 [mpeg2video @ 0xb72f2764]mb incr damaged
2009-01-04 19:21:53.886 [mpeg2video @ 0xb72f2764]mb incr damaged
2009-01-04 19:21:53.886 [mpeg2video @ 0xb72f2764]slice mismatch
2009-01-04 19:21:53.886 [mpeg2video @ 0xb72f2764]ac-tex damaged at 0 27
2009-01-04 19:21:53.887 [mpeg2video @ 0xb72f2764]ac-tex damaged at 0 28
2009-01-04 19:21:53.887 [mpeg2video @ 0xb72f2764]ac-tex damaged at 0 29
2009-01-04 19:21:53.941 TV: Attempting to change from WatchingPreRecorded to None
2009-01-04 19:21:53.953 [ac3 @ 0xb72f2764]frame CRC mismatch
2009-01-04 19:21:53.954 [ac3 @ 0xb72f2764]frame CRC mismatch
2009-01-04 19:21:54.020 TV: Changing from WatchingPreRecorded to None
2009-01-04 19:21:55.031 DPMS Reactivated.
2009-01-04 19:21:57.629 Deleting UPnP client...

```

I used the mythbuntu log grabber to get the logs.  Not sure if this gives me everything though?

---

### Post by newlinux on 2009-01-04
no that's not everything, should start with at least "Attempting to change from None to WatchingPreRecorded" 

Can you play the dvd using a different application like VLC?

---

### Post by murbanci on 2009-01-04
> **newlinux said:**
> no that's not everything, should start with at least "Attempting to change from None to WatchingPreRecorded" 

Ok so here is the log. I viewed it with tail as I tried to watch the movie.  At the end of the this block it seems to complain about some kind of protection:

```

2009-01-04 20:26:22.209 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-01-04 20:26:22.210 Using protocol version 40
2009-01-04 20:26:22.220 TV: Attempting to change from None to WatchingPreRecorded
libdvdread: Using libdvdcss version 1.2.10 for DVD access

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x000001e0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00021f20
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0004b0b3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x002335c0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x002335e0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x002d4d00
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002d4d20
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x002d8920
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x002d8940
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x002f4800
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x002f4820
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x002f5de0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x002f5e00
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x002ff520
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x002ff540
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x00309c00
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x00309c20
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x0030ffa0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x0030ffc0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_09_1.VOB (0x0030ffc0)!!
libdvdread: Elapsed time 18
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x0031a280
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x0031a2a0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_10_1.VOB (0x0031a2a0)!!
libdvdread: Elapsed time 5
libdvdread: Get key for /VIDEO_TS/VTS_11_0.VOB at 0x0031f6e0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_11_0.VOB (0x0031f6e0)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x0031f7a0
libdvdread: Elapsed time 0
libdvdread: Found 11 VTS's
libdvdread: Elapsed time 23
libdvdnav: Using dvdnav version 0.1.10-xine from http://xine.sf.net
libdvdnav: DVD Title: DVD_VIDEO
libdvdnav: DVD Serial Number: 2D338477
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/murbancic/.dvdnav/DVD VIDEO.map'
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8
2009-01-04 20:26:50.924 Opened DVD device at /dev/dvd1
libdvdnav: Suspected RCE Region Protection!!!

```


```

2009-01-04 20:26:50.924 There are 24 titles on the disk
2009-01-04 20:26:50.924 Title 0 has 0 parts.
2009-01-04 20:26:50.924 Title 1 has 28 parts.
2009-01-04 20:26:50.924 Title 2 has 2 parts.
2009-01-04 20:26:50.924 Title 3 has 2 parts.
2009-01-04 20:26:50.924 Title 4 has 2 parts.
2009-01-04 20:26:50.924 Title 5 has 2 parts.
2009-01-04 20:26:50.924 Title 6 has 2 parts.
2009-01-04 20:26:50.925 Title 7 has 2 parts.
2009-01-04 20:26:50.925 Title 8 has 2 parts.
2009-01-04 20:26:50.925 Title 9 has 2 parts.
2009-01-04 20:26:50.925 Title 10 has 2 parts.
2009-01-04 20:26:50.925 Title 11 has 2 parts.
2009-01-04 20:26:50.925 Title 12 has 2 parts.
2009-01-04 20:26:50.925 Title 13 has 2 parts.
2009-01-04 20:26:50.925 Title 14 has 2 parts.
2009-01-04 20:26:50.925 Title 15 has 2 parts.
2009-01-04 20:26:50.925 Title 16 has 2 parts.
2009-01-04 20:26:50.925 Title 17 has 2 parts.
2009-01-04 20:26:50.925 Title 18 has 2 parts.
2009-01-04 20:26:50.925 Title 19 has 2 parts.
2009-01-04 20:26:50.925 Title 20 has 2 parts.
2009-01-04 20:26:50.925 Title 21 has 2 parts.
2009-01-04 20:26:50.925 Title 22 has 2 parts.
2009-01-04 20:26:50.925 Title 23 has 2 parts.
2009-01-04 20:26:50.959 DPMS Deactivated 
2009-01-04 20:26:51.130 AFD: Opened codec 0x9a3b990, id(MPEG2VIDEO) type(Video)
2009-01-04 20:26:51.130 NVP: Disabling Audio, params(-1,-1,-1)
2009-01-04 20:26:51.167 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-01-04 20:26:51.210 OSD Theme Dimensions W: 640 H: 480
2009-01-04 20:26:51.658 TV: Changing from None to WatchingPreRecorded
2009-01-04 20:26:51.661 New DB connection, total: 3
2009-01-04 20:26:51.663 Connected to database 'mythconverg' at host: localhost
2009-01-04 20:26:51.766 Video timing method: USleep with busy wait
2009-01-04 20:26:51.855 AFD: Warning, video codec 0x9a3b990 id(MPEG2VIDEO) type (Video) already open.
2009-01-04 20:26:51.986 AFD: codec AC3 has 0 channels
2009-01-04 20:26:52.003 AFD: Opened codec 0xb2518790, id(AC3) type(Audio)
2009-01-04 20:26:52.007 Opening audio device 'default'. ch 2(2) sr 48000
2009-01-04 20:26:52.007 Opening ALSA audio device 'default'.
2009-01-04 20:26:52.107 mixer unable to find control Master 1
2009-01-04 20:26:52.108 NVP: Enabling Audio
2009-01-04 20:26:52.108 AFD: Warning, audio codec 0xb2518790 id(AC3) type (Audio) already open, leaving it alone.
2009-01-04 20:26:52.108 AFD: codec AC3 has 2 channels
libdvdnav: Suspected RCE Region Protection!!!
2009-01-04 20:27:25.541 AFD: Warning, video codec 0x9a3b990 id(MPEG2VIDEO) type (Video) already open.
2009-01-04 20:27:25.555 AFD: Opened codec 0xa8032430, id(DVD_SUBTITLE) type(Subtitle)
2009-01-04 20:27:25.555 NVP: Disabling Audio, params(-1,-1,-1)
2009-01-04 20:27:25.561 AFD: Warning, video codec 0x9a3b990 id(MPEG2VIDEO) type (Video) already open.
2009-01-04 20:27:25.562 AFD: Opened codec 0xa8c91920, id(DVD_SUBTITLE) type(Subtitle)
2009-01-04 20:27:25.565 AFD: Warning, video codec 0x9a3b990 id(MPEG2VIDEO) type (Video) already open.
2009-01-04 20:27:25.565 AFD: codec AC3 has 0 channels
2009-01-04 20:27:25.566 AFD: Opened codec 0xa8cb6930, id(AC3) type(Audio)
2009-01-04 20:27:25.581 Opening audio device 'default'. ch 2(2) sr 48000
2009-01-04 20:27:25.581 Opening ALSA audio device 'default'.
2009-01-04 20:27:25.624 mixer unable to find control Master 1
2009-01-04 20:27:25.624 NVP: Enabling Audio
2009-01-04 20:27:25.624 [mpeg2video @ 0xb73ba764]00 motion_type at 32 7
2009-01-04 20:27:25.624 [mpeg2video @ 0xb73ba764]00 motion_type at 2 8
2009-01-04 20:27:25.624 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 9
2009-01-04 20:27:25.625 [mpeg2video @ 0xb73ba764]00 motion_type at 15 10
2009-01-04 20:27:25.625 [mpeg2video @ 0xb73ba764]00 motion_type at 4 11
2009-01-04 20:27:25.625 [mpeg2video @ 0xb73ba764]ac-tex damaged at 10 12
2009-01-04 20:27:25.625 [mpeg2video @ 0xb73ba764]00 motion_type at 9 13
2009-01-04 20:27:25.625 [mpeg2video @ 0xb73ba764]00 motion_type at 15 14
2009-01-04 20:27:25.625 [mpeg2video @ 0xb73ba764]00 motion_type at 4 15
2009-01-04 20:27:25.625 [mpeg2video @ 0xb73ba764]invalid cbp at 9 16
2009-01-04 20:27:25.625 [mpeg2video @ 0xb73ba764]mb incr damaged
2009-01-04 20:27:25.626 [mpeg2video @ 0xb73ba764]00 motion_type at 17 19
2009-01-04 20:27:25.626 [mpeg2video @ 0xb73ba764]ac-tex damaged at 9 20
2009-01-04 20:27:25.626 [mpeg2video @ 0xb73ba764]invalid mb type in P Frame at 3 21
2009-01-04 20:27:25.626 [mpeg2video @ 0xb73ba764]ac-tex damaged at 23 22
2009-01-04 20:27:25.626 [mpeg2video @ 0xb73ba764]00 motion_type at 14 23
2009-01-04 20:27:25.626 [mpeg2video @ 0xb73ba764]00 motion_type at 4 24
2009-01-04 20:27:25.626 [mpeg2video @ 0xb73ba764]00 motion_type at 4 25
2009-01-04 20:27:25.627 [mpeg2video @ 0xb73ba764]00 motion_type at 3 26
2009-01-04 20:27:25.627 [mpeg2video @ 0xb73ba764]00 motion_type at 25 27
2009-01-04 20:27:25.627 [mpeg2video @ 0xb73ba764]ac-tex damaged at 8 28
2009-01-04 20:27:25.627 [mpeg2video @ 0xb73ba764]invalid mb type in P Frame at 3 29
2009-01-04 20:27:25.627 [mpeg2video @ 0xb73ba764]Warning MVs not available

```

From this point down is after I click play from the DVD menu.  Up until this point everything looks and works fine.

```

2009-01-04 20:27:35.230 [ac3 @ 0xb73ba764]frame CRC mismatch
2009-01-04 20:27:35.233 [mpeg2video @ 0xb73ba764]ac-tex damaged at 18 0
2009-01-04 20:27:35.427 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
libdvdnav: Suspected RCE Region Protection!!!
2009-01-04 20:27:39.033 [ac3 @ 0xb73ba764]frame CRC mismatch
libdvdnav: Suspected RCE Region Protection!!!
libdvdnav: Suspected RCE Region Protection!!!
2009-01-04 20:28:04.152 AFD: Warning, video codec 0x9a3b990 id(MPEG2VIDEO) type (Video) already open.
2009-01-04 20:28:04.152 NVP: Disabling Audio, params(-1,-1,-1)
2009-01-04 20:28:04.158 AFD: Warning, video codec 0x9a3b990 id(MPEG2VIDEO) type (Video) already open.
2009-01-04 20:28:04.158 AFD: codec AC3 has 0 channels
2009-01-04 20:28:04.159 AFD: Opened codec 0xa802b8c0, id(AC3) type(Audio)
2009-01-04 20:28:04.162 AFD: Warning, video codec 0x9a3b990 id(MPEG2VIDEO) type (Video) already open.
2009-01-04 20:28:04.163 AFD: Warning, audio codec 0xa802b8c0 id(AC3) type (Audio) already open, leaving it alone.
2009-01-04 20:28:04.163 AFD: codec AC3 has 6 channels
2009-01-04 20:28:04.163 AFD: codec AC3 has 0 channels
2009-01-04 20:28:04.164 AFD: Opened codec 0xa8c9d750, id(AC3) type(Audio)
2009-01-04 20:28:04.164 NVP: Disabling Audio, params(0,0,0)
2009-01-04 20:28:04.167 Opening audio device 'default'. ch 2(2) sr 48000
2009-01-04 20:28:04.167 Opening ALSA audio device 'default'.
2009-01-04 20:28:04.207 mixer unable to find control Master 1
2009-01-04 20:28:04.207 NVP: Enabling Audio
2009-01-04 20:28:04.208 [ac3 @ 0xb73ba764]frame CRC mismatch
2009-01-04 20:28:04.212 AFD: Warning, video codec 0x9a3b990 id(MPEG2VIDEO) type (Video) already open.
2009-01-04 20:28:04.212 AFD: Warning, audio codec 0xa802b8c0 id(AC3) type (Audio) already open, leaving it alone.
2009-01-04 20:28:04.212 AFD: codec AC3 has 6 channels
2009-01-04 20:28:04.212 AFD: Warning, audio codec 0xa8c9d750 id(AC3) type (Audio) already open, leaving it alone.
2009-01-04 20:28:04.213 AFD: codec AC3 has 2 channels
2009-01-04 20:28:04.213 AFD: codec AC3 has 0 channels
2009-01-04 20:28:04.213 AFD: Opened codec 0xa8030c90, id(AC3) type(Audio)
2009-01-04 20:28:04.245 NVP: prebuffering pause
2009-01-04 20:28:04.385 AFD: Warning, audio codec 0xa802b8c0 id(AC3) type (Audio) already open, leaving it alone.
2009-01-04 20:28:04.385 AFD: codec AC3 has 6 channels
2009-01-04 20:28:04.385 AFD: Warning, audio codec 0xa8c9d750 id(AC3) type (Audio) already open, leaving it alone.
2009-01-04 20:28:04.385 AFD: codec AC3 has 2 channels
2009-01-04 20:28:04.385 AFD: Warning, audio codec 0xa8030c90 id(AC3) type (Audio) already open, leaving it alone.
2009-01-04 20:28:04.386 AFD: codec AC3 has 2 channels
2009-01-04 20:28:04.541 [mpeg2video @ 0xb73ba764]mb incr damaged
2009-01-04 20:28:04.542 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 8
2009-01-04 20:28:04.542 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 9
2009-01-04 20:28:04.542 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 10
2009-01-04 20:28:04.542 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 11
2009-01-04 20:28:04.542 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 12
2009-01-04 20:28:04.542 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 13
2009-01-04 20:28:04.542 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 14
2009-01-04 20:28:04.542 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 15
2009-01-04 20:28:04.543 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 16
2009-01-04 20:28:04.543 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 17
2009-01-04 20:28:04.543 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 18
2009-01-04 20:28:04.543 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 19
2009-01-04 20:28:04.543 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 20
2009-01-04 20:28:04.543 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 21
2009-01-04 20:28:04.543 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 22
2009-01-04 20:28:04.543 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 23
2009-01-04 20:28:04.543 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 24
2009-01-04 20:28:04.544 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 25
2009-01-04 20:28:04.544 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 26
2009-01-04 20:28:04.544 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 27
2009-01-04 20:28:04.544 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 28
2009-01-04 20:28:04.544 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 29
2009-01-04 20:28:04.544 [mpeg2video @ 0xb73ba764]Warning MVs not available
2009-01-04 20:28:04.549 [mpeg2video @ 0xb73ba764]sequence header damaged
2009-01-04 20:28:04.549 [mpeg2video @ 0xb73ba764]slice mismatch
2009-01-04 20:28:04.550 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 8
2009-01-04 20:28:04.550 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 9
2009-01-04 20:28:04.550 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 10
2009-01-04 20:28:04.550 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 11
2009-01-04 20:28:04.550 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 12
2009-01-04 20:28:04.550 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 13
2009-01-04 20:28:04.550 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 14
2009-01-04 20:28:04.550 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 15
2009-01-04 20:28:04.550 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 16
2009-01-04 20:28:04.551 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 17
2009-01-04 20:28:04.551 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 18
2009-01-04 20:28:04.551 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 19
2009-01-04 20:28:04.551 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 20
2009-01-04 20:28:04.551 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 21
2009-01-04 20:28:04.551 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 22
2009-01-04 20:28:04.551 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 23
2009-01-04 20:28:04.551 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 24
2009-01-04 20:28:04.551 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 25
2009-01-04 20:28:04.551 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 26
2009-01-04 20:28:04.552 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 27
2009-01-04 20:28:04.552 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 28
2009-01-04 20:28:04.552 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 29
2009-01-04 20:28:04.556 [mpeg2video @ 0xb73ba764]sequence header damaged
2009-01-04 20:28:04.557 [mpeg2video @ 0xb73ba764]slice mismatch
2009-01-04 20:28:04.557 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 8
2009-01-04 20:28:04.557 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 9
2009-01-04 20:28:04.557 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 10
2009-01-04 20:28:04.557 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 11
2009-01-04 20:28:04.558 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 12
2009-01-04 20:28:04.558 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 13
2009-01-04 20:28:04.558 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 14
2009-01-04 20:28:04.558 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 15
2009-01-04 20:28:04.558 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 16
2009-01-04 20:28:04.558 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 17
2009-01-04 20:28:04.558 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 18
2009-01-04 20:28:04.558 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 19
2009-01-04 20:28:04.558 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 20
2009-01-04 20:28:04.559 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 21
2009-01-04 20:28:04.559 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 22
2009-01-04 20:28:04.559 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 23
2009-01-04 20:28:04.559 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 24
2009-01-04 20:28:04.559 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 25
2009-01-04 20:28:04.559 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 26
2009-01-04 20:28:04.559 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 27
2009-01-04 20:28:04.559 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 28
2009-01-04 20:28:04.559 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 29
2009-01-04 20:28:04.564 [mpeg2video @ 0xb73ba764]sequence header damaged
2009-01-04 20:28:04.565 [mpeg2video @ 0xb73ba764]slice mismatch
2009-01-04 20:28:04.565 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 8
2009-01-04 20:28:04.565 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 9
2009-01-04 20:28:04.565 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 10
2009-01-04 20:28:04.565 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 11
2009-01-04 20:28:04.565 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 12
2009-01-04 20:28:04.565 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 13
2009-01-04 20:28:04.566 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 14
2009-01-04 20:28:04.566 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 15
2009-01-04 20:28:04.566 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 16
2009-01-04 20:28:04.566 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 17
2009-01-04 20:28:04.566 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 18
2009-01-04 20:28:04.566 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 19
2009-01-04 20:28:04.566 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 20
2009-01-04 20:28:04.566 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 21
2009-01-04 20:28:04.566 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 22
2009-01-04 20:28:04.566 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 23
2009-01-04 20:28:04.567 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 24
2009-01-04 20:28:04.567 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 25
2009-01-04 20:28:04.567 [mpeg2video @ 0xb73ba764]ac-tex damaged at 1 26
2009-01-04 20:28:04.567 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 27
2009-01-04 20:28:04.567 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 28
2009-01-04 20:28:04.567 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 29
2009-01-04 20:28:04.571 [ac3 @ 0xb73ba764]frame CRC mismatch
2009-01-04 20:28:04.577 [mpeg2video @ 0xb73ba764]sequence header damaged
2009-01-04 20:28:04.589 [ac3 @ 0xb73ba764]frame CRC mismatch
2009-01-04 20:28:04.597 [mpeg2video @ 0xb73ba764]sequence header damaged
2009-01-04 20:28:04.597 [mpeg2video @ 0xb73ba764]mb incr damaged
2009-01-04 20:28:04.597 [mpeg2video @ 0xb73ba764]ac-tex damaged at 3 15
2009-01-04 20:28:04.598 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 16
2009-01-04 20:28:04.598 [mpeg2video @ 0xb73ba764]00 motion_type at 5 17
2009-01-04 20:28:04.598 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 18
2009-01-04 20:28:04.598 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 19
2009-01-04 20:28:04.598 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 20
2009-01-04 20:28:04.598 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 21
2009-01-04 20:28:04.598 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 22
2009-01-04 20:28:04.598 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 23
2009-01-04 20:28:04.598 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 24
2009-01-04 20:28:04.598 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 25
2009-01-04 20:28:04.599 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 26
2009-01-04 20:28:04.599 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 27
2009-01-04 20:28:04.599 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 28
2009-01-04 20:28:04.599 [mpeg2video @ 0xb73ba764]ac-tex damaged at 0 29
2009-01-04 20:28:04.694 [ac3 @ 0xb73ba764]frame CRC mismatch
2009-01-04 20:28:04.699 [mpeg2video @ 0xb73ba764]sequence header damaged
2009-01-04 20:28:04.699 [mpeg2video @ 0xb73ba764]ac-tex damaged at 10 10
2009-01-04 20:28:04.699 [mpeg2video @ 0xb73ba764]slice mismatch
2009-01-04 20:28:04.700 [mpeg2video @ 0xb73ba764]slice mismatch
2009-01-04 20:28:04.700 [mpeg2video @ 0xb73ba764]invalid mb type in B Frame at 27 3
2009-01-04 20:28:04.700 [mpeg2video @ 0xb73ba764]ac-tex damaged at 24 7
2009-01-04 20:28:04.700 [mpeg2video @ 0xb73ba764]slice mismatch
2009-01-04 20:28:04.700 [mpeg2video @ 0xb73ba764]invalid cbp at 39 9
2009-01-04 20:28:04.700 [mpeg2video @ 0xb73ba764]invalid mb type in B Frame at 27 13
2009-01-04 20:28:04.700 [mpeg2video @ 0xb73ba764]invalid mb type in B Frame at 6 14
2009-01-04 20:28:04.700 [mpeg2video @ 0xb73ba764]invalid mb type in B Frame at 30 14
2009-01-04 20:28:04.701 [mpeg2video @ 0xb73ba764]slice mismatch
2009-01-04 20:28:04.701 [mpeg2video @ 0xb73ba764]ac-tex damaged at 20 20
2009-01-04 20:28:04.701 [mpeg2video @ 0xb73ba764]mb incr damaged
2009-01-04 20:28:04.701 [mpeg2video @ 0xb73ba764]slice mismatch
2009-01-04 20:28:04.701 [mpeg2video @ 0xb73ba764]ac-tex damaged at 19 26
2009-01-04 20:28:04.701 [mpeg2video @ 0xb73ba764]mb incr damaged
2009-01-04 20:28:04.701 [mpeg2video @ 0xb73ba764]Warning MVs not available
2009-01-04 20:28:04.705 [mpeg2video @ 0xb73ba764]ac-tex damaged at 12 2
2009-01-04 20:28:04.705 [mpeg2video @ 0xb73ba764]ac-tex damaged at 35 7
2009-01-04 20:28:04.705 [mpeg2video @ 0xb73ba764]mb incr damaged
2009-01-04 20:28:04.706 [mpeg2video @ 0xb73ba764]ac-tex damaged at 38 18
2009-01-04 20:28:04.706 [mpeg2video @ 0xb73ba764]ac-tex damaged at 30 24
2009-01-04 20:28:04.707 [mpeg2video @ 0xb73ba764]end mismatch left=428011 773230
2009-01-04 20:28:04.707 [mpeg2video @ 0xb73ba764]ac-tex damaged at 16 1
2009-01-04 20:28:04.707 [mpeg2video @ 0xb73ba764]invalid mb type in B Frame at 25 3
2009-01-04 20:28:04.707 [mpeg2video @ 0xb73ba764]ac-tex damaged at 33 4
2009-01-04 20:28:04.707 [mpeg2video @ 0xb73ba764]slice mismatch
2009-01-04 20:28:04.707 [mpeg2video @ 0xb73ba764]invalid mb type in B Frame at 3 10
2009-01-04 20:28:04.707 [mpeg2video @ 0xb73ba764]mb incr damaged
2009-01-04 20:28:04.707 [mpeg2video @ 0xb73ba764]mb incr damaged
2009-01-04 20:28:04.707 [mpeg2video @ 0xb73ba764]ac-tex damaged at 6 16
2009-01-04 20:28:04.707 [mpeg2video @ 0xb73ba764]mb incr damaged
2009-01-04 20:28:04.708 [mpeg2video @ 0xb73ba764]invalid cbp at 37 20
2009-01-04 20:28:04.708 [mpeg2video @ 0xb73ba764]ac-tex damaged at 25 21
2009-01-04 20:28:04.708 [mpeg2video @ 0xb73ba764]mb incr damaged
2009-01-04 20:28:04.708 [mpeg2video @ 0xb73ba764]mb incr damaged
2009-01-04 20:28:04.708 [mpeg2video @ 0xb73ba764]slice mismatch
2009-01-04 20:28:04.708 [mpeg2video @ 0xb73ba764]invalid mb type in B Frame at 6 29
2009-01-04 20:28:04.712 [mpeg2video @ 0xb73ba764]ac-tex damaged at 24 1
2009-01-04 20:28:04.713 [mpeg2video @ 0xb73ba764]ac-tex damaged at 12 5
2009-01-04 20:28:04.713 [mpeg2video @ 0xb73ba764]mb incr damaged
2009-01-04 20:28:04.714 [mpeg2video @ 0xb73ba764]mb incr damaged
2009-01-04 20:28:04.714 [mpeg2video @ 0xb73ba764]ac-tex damaged at 23 16
2009-01-04 20:28:04.714 [mpeg2video @ 0xb73ba764]ac-tex damaged at 40 20
2009-01-04 20:28:04.715 [mpeg2video @ 0xb73ba764]ac-tex damaged at 6 25
2009-01-04 20:28:04.715 [mpeg2video @ 0xb73ba764]ac-tex damaged at 13 29
2009-01-04 20:28:04.715 [mpeg2video @ 0xb73ba764]invalid cbp at 32 2
2009-01-04 20:28:04.715 [mpeg2video @ 0xb73ba764]invalid cbp at 11 3
2009-01-04 20:28:04.715 [mpeg2video @ 0xb73ba764]mb incr damaged
2009-01-04 20:28:04.715 [mpeg2video @ 0xb73ba764]slice mismatch
2009-01-04 20:28:04.716 [mpeg2video @ 0xb73ba764]slice mismatch
2009-01-04 20:28:04.716 [mpeg2video @ 0xb73ba764]slice mismatch
2009-01-04 20:28:04.716 [mpeg2video @ 0xb73ba764]ac-tex damaged at 19 10
2009-01-04 20:28:04.716 [mpeg2video @ 0xb73ba764]invalid mb type in B Frame at 23 11
2009-01-04 20:28:04.716 [mpeg2video @ 0xb73ba764]invalid mb type in B Frame at 28 13
2009-01-04 20:28:04.716 [mpeg2video @ 0xb73ba764]ac-tex damaged at 28 14
2009-01-04 20:28:04.716 [mpeg2video @ 0xb73ba764]mb incr damaged
2009-01-04 20:28:04.716 [mpeg2video @ 0xb73ba764]invalid mb type in B Frame at 25 16
2009-01-04 20:28:04.716 [mpeg2video @ 0xb73ba764]ac-tex damaged at 13 17
2009-01-04 20:28:04.716 [mpeg2video @ 0xb73ba764]invalid cbp at 9 20
2009-01-04 20:28:04.716 [mpeg2video @ 0xb73ba764]ac-tex damaged at 7 21
2009-01-04 20:28:04.717 [mpeg2video @ 0xb73ba764]slice mismatch
2009-01-04 20:28:04.717 [mpeg2video @ 0xb73ba764]slice mismatch
2009-01-04 20:28:04.717 [mpeg2video @ 0xb73ba764]slice mismatch
2009-01-04 20:28:04.721 [mpeg2video @ 0xb73ba764]invalid mb type in P Frame at 42 0
2009-01-04 20:28:04.722 [mpeg2video @ 0xb73ba764]ac-tex damaged at 17 2
2009-01-04 20:28:04.722 [mpeg2video @ 0xb73ba764]ac-tex damaged at 27 5
2009-01-04 20:28:04.722 [mpeg2video @ 0xb73ba764]ac-tex damaged at 22 7
2009-01-04 20:28:04.774 [ac3 @ 0xb73ba764]frame CRC mismatch
2009-01-04 20:28:04.780 [mpeg2video @ 0xb73ba764]sequence header damaged
2009-01-04 20:28:04.781 [mpeg2video @ 0xb73ba764]ac-tex damaged at 18 5
2009-01-04 20:28:04.782 [mpeg2video @ 0xb73ba764]ac-tex damaged at 8 10
2009-01-04 20:28:04.782 [mpeg2video @ 0xb73ba764]ac-tex damaged at 31 15
2009-01-04 20:28:04.783 [mpeg2video @ 0xb73ba764]ac-tex damaged at 38 20
2009-01-04 20:28:04.783 [mpeg2video @ 0xb73ba764]ac-tex damaged at 1 27
2009-01-04 20:28:04.788 [mpeg2video @ 0xb73ba764]invalid cbp at 12 2
2009-01-04 20:28:04.788 [mpeg2video @ 0xb73ba764]ac-tex damaged at 32 7
2009-01-04 20:28:04.789 [mpeg2video @ 0xb73ba764]invalid cbp at 20 13
2009-01-04 20:28:04.789 [mpeg2video @ 0xb73ba764]ac-tex damaged at 24 19
2009-01-04 20:28:04.790 [mpeg2video @ 0xb73ba764]invalid mb type in B Frame at 16 27
2009-01-04 20:28:04.790 [mpeg2video @ 0xb73ba764]mb incr damaged
2009-01-04 20:28:04.790 [mpeg2video @ 0xb73ba764]invalid cbp at 0 3
2009-01-04 20:28:04.790 [mpeg2video @ 0xb73ba764]invalid cbp at 0 4
2009-01-04 20:28:04.790 [mpeg2video @ 0xb73ba764]slice mismatch
2009-01-04 20:28:04.790 [mpeg2video @ 0xb73ba764]slice mismatch
2009-01-04 20:28:04.790 [mpeg2video @ 0xb73ba764]slice mismatch
2009-01-04 20:28:04.790 [mpeg2video @ 0xb73ba764]slice mismatch
2009-01-04 20:28:04.790 [mpeg2video @ 0xb73ba764]slice mismatch
2009-01-04 20:28:04.790 [mpeg2video @ 0xb73ba764]slice mismatch
2009-01-04 20:28:04.790 [mpeg2video @ 0xb73ba764]slice mismatch
2009-01-04 20:28:04.790 [mpeg2video @ 0xb73ba764]slice mismatch
2009-01-04 20:28:04.790 [mpeg2video @ 0xb73ba764]mb incr damaged
2009-01-04 20:28:04.790 [mpeg2video @ 0xb73ba764]ac-tex damaged at 5 22
2009-01-04 20:28:04.790 [mpeg2video @ 0xb73ba764]slice mismatch
2009-01-04 20:28:04.791 [mpeg2video @ 0xb73ba764]slice mismatch
2009-01-04 20:28:04.791 [mpeg2video @ 0xb73ba764]mb incr damaged
2009-01-04 20:28:04.791 [mpeg2video @ 0xb73ba764]ac-tex damaged at 38 28
2009-01-04 20:28:04.797 [ac3 @ 0xb73ba764]frame CRC mismatch
2009-01-04 20:28:04.798 [mpeg2video @ 0xb73ba764]invalid mb type in B Frame at 26 7
2009-01-04 20:28:04.799 [mpeg2video @ 0xb73ba764]invalid cbp at 34 13
2009-01-04 20:28:04.799 [mpeg2video @ 0xb73ba764]ac-tex damaged at 24 19
2009-01-04 20:28:04.800 [mpeg2video @ 0xb73ba764]invalid mb type in B Frame at 15 26
2009-01-04 20:28:04.806 [mpeg2video @ 0xb73ba764]invalid cbp at 33 5
2009-01-04 20:28:04.806 [mpeg2video @ 0xb73ba764]ac-tex damaged at 35 11
2009-01-04 20:28:04.807 [mpeg2video @ 0xb73ba764]invalid cbp at 39 17
2009-01-04 20:28:04.807 [mpeg2video @ 0xb73ba764]ac-tex damaged at 22 24
2009-01-04 20:28:04.814 [mpeg2video @ 0xb73ba764]ac-tex damaged at 33 0
2009-01-04 20:28:04.814 [mpeg2video @ 0xb73ba764]mb incr damaged
2009-01-04 20:28:04.814 [mpeg2video @ 0xb73ba764]ac-tex damaged at 7 7
2009-01-04 20:28:04.815 [mpeg2video @ 0xb73ba764]ac-tex damaged at 21 11
2009-01-04 20:28:04.815 [mpeg2video @ 0xb73ba764]ac-tex damaged at 2 14
2009-01-04 20:28:04.815 [mpeg2video @ 0xb73ba764]ac-tex damaged at 29 17
2009-01-04 20:28:04.815 [mpeg2video @ 0xb73ba764]ac-tex damaged at 20 20
2009-01-04 20:28:04.815 [mpeg2video @ 0xb73ba764]ac-tex damaged at 23 24
2009-01-04 20:28:04.878 [ac3 @ 0xb73ba764]frame CRC mismatch
2009-01-04 20:28:04.884 [mpeg2video @ 0xb73ba764]sequence header damaged
2009-01-04 20:28:04.884 [mpeg2video @ 0xb73ba764]mb incr damaged
2009-01-04 20:28:04.884 [mpeg2video @ 0xb73ba764]slice mismatch
2009-01-04 20:28:04.885 [mpeg2video @ 0xb73ba764]invalid cbp at 3 26
2009-01-04 20:28:04.885 [mpeg2video @ 0xb73ba764]ac-tex damaged at 38 26
2009-01-04 20:28:04.885 [mpeg2video @ 0xb73ba764]mb incr damaged
2009-01-04 20:28:04.889 [mpeg2video @ 0xb73ba764]invalid mb type in B Frame at 5 4
2009-01-04 20:28:04.890 [mpeg2video @ 0xb73ba764]ac-tex damaged at 17 14
2009-01-04 20:28:04.891 [mpeg2video @ 0xb73ba764]ac-tex damaged at 26 19
2009-01-04 20:28:04.892 [mpeg2video @ 0xb73ba764]mb incr damaged
2009-01-04 20:28:04.898 [ac3 @ 0xb73ba764]frame CRC mismatch
2009-01-04 20:28:04.900 [mpeg2video @ 0xb73ba764]ac-tex damaged at 20 1
2009-01-04 20:28:04.901 [mpeg2video @ 0xb73ba764]slice mismatch
2009-01-04 20:28:04.901 [mpeg2video @ 0xb73ba764]ac-tex damaged at 29 12
2009-01-04 20:28:04.902 [mpeg2video @ 0xb73ba764]ac-tex damaged at 34 17
2009-01-04 20:28:04.902 [mpeg2video @ 0xb73ba764]ac-tex damaged at 3 23
2009-01-04 20:28:04.903 [mpeg2video @ 0xb73ba764]ac-tex damaged at 5 28
2009-01-04 20:28:04.903 [mpeg2video @ 0xb73ba764]mb incr damaged
2009-01-04 20:28:04.903 [mpeg2video @ 0xb73ba764]ac-tex damaged at 9 2
2009-01-04 20:28:04.903 [mpeg2video @ 0xb73ba764]slice mismatch
2009-01-04 20:28:04.903 [mpeg2video @ 0xb73ba764]mb incr damaged
2009-01-04 20:28:04.903 [mpeg2video @ 0xb73ba764]invalid mb type in B Frame at 42 6
2009-01-04 20:28:04.903 [mpeg2video @ 0xb73ba764]mb incr damaged
2009-01-04 20:28:04.903 [mpeg2video @ 0xb73ba764]mb incr damaged
2009-01-04 20:28:04.903 [mpeg2video @ 0xb73ba764]slice mismatch
2009-01-04 20:28:04.903 [mpeg2video @ 0xb73ba764]slice mismatch
2009-01-04 20:28:04.903 [mpeg2video @ 0xb73ba764]slice mismatch
2009-01-04 20:28:04.903 [mpeg2video @ 0xb73ba764]mb incr damaged
2009-01-04 20:28:04.903 [mpeg2video @ 0xb73ba764]slice mismatch
2009-01-04 20:28:04.904 [mpeg2video @ 0xb73ba764]mb incr damaged
2009-01-04 20:28:04.904 [mpeg2video @ 0xb73ba764]mb incr damaged
2009-01-04 20:28:04.904 [mpeg2video @ 0xb73ba764]invalid mb type in B Frame at 15 26
2009-01-04 20:28:04.904 [mpeg2video @ 0xb73ba764]mb incr damaged
2009-01-04 20:28:04.904 [mpeg2video @ 0xb73ba764]mb incr damaged
2009-01-04 20:28:04.904 [mpeg2video @ 0xb73ba764]ac-tex damaged at 11 2
2009-01-04 20:28:04.904 [mpeg2video @ 0xb73ba764]invalid mb type in B Frame at 4 3
2009-01-04 20:28:04.904 [mpeg2video @ 0xb73ba764]mb incr damaged
2009-01-04 20:28:04.904 [mpeg2video @ 0xb73ba764]invalid mb type in B Frame at 26 8
2009-01-04 20:28:04.904 [mpeg2video @ 0xb73ba764]invalid mb type in B Frame at 22 9
2009-01-04 20:28:04.904 [mpeg2video @ 0xb73ba764]mb incr damaged
2009-01-04 20:28:04.905 [mpeg2video @ 0xb73ba764]ac-tex damaged at 38 14
2009-01-04 20:28:04.905 [mpeg2video @ 0xb73ba764]ac-tex damaged at 5 14
2009-01-04 20:28:04.905 [mpeg2video @ 0xb73ba764]slice mismatch
2009-01-04 20:28:04.905 [mpeg2video @ 0xb73ba764]ac-tex damaged at 26 18
2009-01-04 20:28:04.905 [mpeg2video @ 0xb73ba764]invalid mb type in B Frame at 34 22
2009-01-04 20:28:04.905 [mpeg2video @ 0xb73ba764]mb incr damaged
2009-01-04 20:28:04.905 [mpeg2video @ 0xb73ba764]mb incr damaged
2009-01-04 20:28:04.905 [mpeg2video @ 0xb73ba764]mb incr damaged
2009-01-04 20:28:04.906 [mpeg2video @ 0xb73ba764]mb incr damaged
2009-01-04 20:28:04.914 [mpeg2video @ 0xb73ba764]ac-tex damaged at 12 8
2009-01-04 20:28:04.914 [mpeg2video @ 0xb73ba764]ac-tex damaged at 22 13
2009-01-04 20:28:04.915 [mpeg2video @ 0xb73ba764]ac-tex damaged at 25 17
2009-01-04 20:28:04.915 [mpeg2video @ 0xb73ba764]ac-tex damaged at 29 24
2009-01-04 20:28:04.916 [mpeg2video @ 0xb73ba764]ac-tex damaged at 7 28
2009-01-04 20:28:04.916 [mpeg2video @ 0xb73ba764]invalid cbp at 25 2
2009-01-04 20:28:04.916 [mpeg2video @ 0xb73ba764]ac-tex damaged at 3 3
2009-01-04 20:28:04.916 [mpeg2video @ 0xb73ba764]slice mismatch
2009-01-04 20:28:04.916 [mpeg2video @ 0xb73ba764]mb incr damaged
2009-01-04 20:28:04.916 [mpeg2video @ 0xb73ba764]mb incr damaged
2009-01-04 20:28:04.916 [mpeg2video @ 0xb73ba764]slice mismatch
2009-01-04 20:28:04.916 [mpeg2video @ 0xb73ba764]invalid mb type in B Frame at 6 12
2009-01-04 20:28:04.917 [mpeg2video @ 0xb73ba764]mb incr damaged
2009-01-04 20:28:04.917 [mpeg2video @ 0xb73ba764]slice mismatch
2009-01-04 20:28:04.917 [mpeg2video @ 0xb73ba764]mb incr damaged
2009-01-04 20:28:04.917 [mpeg2video @ 0xb73ba764]mb incr damaged
2009-01-04 20:28:04.917 [mpeg2video @ 0xb73ba764]slice mismatch
2009-01-04 20:28:04.917 [mpeg2video @ 0xb73ba764]mb incr damaged
2009-01-04 20:28:04.917 [mpeg2video @ 0xb73ba764]mb incr damaged
2009-01-04 20:28:04.917 [mpeg2video @ 0xb73ba764]ac-tex damaged at 12 28

```

Hope this helps more.


>  Can you play the dvd using a different application like VLC?

The same thing happens with VLC.  The menu works fine, then when I click play movie and I get a blank screen and garbled audio.

---

### Post by newlinux on 2009-01-04
Sounds like this is an CSS problem, not a myth problem. Have you installed libdvdcss2? Can you play other dvds?
[http://ubuntuguide.org/wiki/Ubuntu:Intrepid#DVD_Playback_Capability](http://ubuntuguide.org/wiki/Ubuntu:Intrepid#DVD_Playback_Capability)

---

### Post by murbanci on 2009-01-04
Its already installed

```

user@mythtv-1:~$ sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdcss2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Some dvds play and some this happens to.

---

### Post by newlinux on 2009-01-04
I'll assume libdvdread3 and libdvdnav4 are also already installed.

Yeah, from what I remember, some discs will still have problems. [http://tobias.rautenkranz.ch/libdvdread_ifo.html](http://tobias.rautenkranz.ch/libdvdread_ifo.html)

 This one, however, may be a problem with the regions. What region is this disc and what region is your drive? You might need to change the region depending on the disc.

You can use regionset to change the drive region. If it reports region = 0xff no region is set. I think some discs may require a region to be set. But i also think you can change the region only so many times - regionset should tell you how many times you can change it. You might be better off trying to rip the dvd and playing the iso.

---

### Post by murbanci on 2009-01-04
yea, they are both installed.  I ran regionset and set the correct code for that and playback seemed to be a little better but still unacceptable.  Ill try to rip an iso and see what happens.

---

### Post by newlinux on 2009-01-04
> **murbanci said:**
> yea, they are both installed.  I ran regionset and set the correct code for that and playback seemed to be a little better but still unacceptable.  Ill try to rip an iso and see what happens.

What was in your logs after the change? Trying to see if that solved any of the problems...

---

### Post by jmig on 2009-01-05
I also have problems with DVD playback from MythTV internal player in my almost standard Mythbuntu install.
The DVD menu does not show up. I can only see the cursor.
Every OSD apears flashing irregulary.
The movie is not pixelaized but goes in steps.
These happends with all DVDs.
MPlayer works perfectly in the same machine.

The mesages I got in log are almost the same as murbanci's:

```

libdvdnav: Using dvdnav version 0.1.10-xine from http://xine.sf.net
libdvdnav: DVD Title: SPIRIT
libdvdnav: DVD Serial Number: 2d3505d0
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/internauta/.dvdnav/SPIRIT.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4
2009-01-05 19:22:23.351 Opened DVD device at /dev/scd1
2009-01-05 19:22:23.352 There are 35 titles on the disk
2009-01-05 19:22:23.352 Title 0 has 0 parts.
2009-01-05 19:22:23.352 Title 1 has 21 parts.
2009-01-05 19:22:23.352 Title 2 has 2 parts.
2009-01-05 19:22:23.352 Title 3 has 2 parts.
2009-01-05 19:22:23.352 Title 4 has 2 parts.
2009-01-05 19:22:23.352 Title 5 has 2 parts.
2009-01-05 19:22:23.352 Title 6 has 2 parts.
2009-01-05 19:22:23.352 Title 7 has 2 parts.
2009-01-05 19:22:23.352 Title 8 has 2 parts.
2009-01-05 19:22:23.352 Title 9 has 2 parts.
2009-01-05 19:22:23.352 Title 10 has 2 parts.
2009-01-05 19:22:23.352 Title 11 has 2 parts.
2009-01-05 19:22:23.352 Title 12 has 2 parts.
2009-01-05 19:22:23.352 Title 13 has 2 parts.
2009-01-05 19:22:23.352 Title 14 has 2 parts.
2009-01-05 19:22:23.352 Title 15 has 2 parts.
2009-01-05 19:22:23.353 Title 16 has 2 parts.
2009-01-05 19:22:23.353 Title 17 has 2 parts.
2009-01-05 19:22:23.353 Title 18 has 2 parts.
2009-01-05 19:22:23.353 Title 19 has 1 parts.
2009-01-05 19:22:23.353 Title 20 has 1 parts.
2009-01-05 19:22:23.353 Title 21 has 1 parts.
2009-01-05 19:22:23.353 Title 22 has 6 parts.
2009-01-05 19:22:23.353 Title 23 has 3 parts.
2009-01-05 19:22:23.353 Title 24 has 3 parts.
2009-01-05 19:22:23.353 Title 25 has 3 parts.
2009-01-05 19:22:23.353 Title 26 has 3 parts.
2009-01-05 19:22:23.353 Title 27 has 3 parts.
2009-01-05 19:22:23.353 Title 28 has 3 parts.
2009-01-05 19:22:23.353 Title 29 has 3 parts.
2009-01-05 19:22:23.353 Title 30 has 3 parts.
2009-01-05 19:22:23.353 Title 31 has 3 parts.
2009-01-05 19:22:23.353 Title 32 has 3 parts.
2009-01-05 19:22:23.354 Title 33 has 3 parts.
2009-01-05 19:22:23.354 Title 34 has 3 parts.
2009-01-05 19:22:23.403 DPMS Deactivated 
2009-01-05 19:22:23.529 AFD: Opened codec 0x8a98850, id(MPEG2VIDEO) type(Video)
2009-01-05 19:22:23.530 NVP: Disabling Audio, params(-1,-1,-1)
2009-01-05 19:22:23.560 VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Video Overlay'
2009-01-05 19:22:23.608 OSD Theme Dimensions W: 640 H: 480
2009-01-05 19:22:23.958 TV: Changing from None to WatchingPreRecorded
2009-01-05 19:22:24.204 DPMS Reactivated.
2009-01-05 19:22:24.305 DPMS Deactivated 
2009-01-05 19:22:24.305 DPMS Reactivated.
2009-01-05 19:22:24.314 Video timing method: USleep with busy wait
2009-01-05 19:22:26.483 AFD: Warning, video codec 0x8a98850 id(MPEG2VIDEO) type (Video) already open.
2009-01-05 19:22:26.509 DPMS Deactivated 
2009-01-05 19:22:26.659 AFD: codec AC3 has 0 channels
2009-01-05 19:22:26.661 AFD: Opened codec 0x9a3bef0, id(AC3) type(Audio)
2009-01-05 19:22:26.667 Opening audio device 'default'. ch 2(2) sr 48000
2009-01-05 19:22:26.667 Opening ALSA audio device 'default'.
2009-01-05 19:22:26.689 mixer unable to find control Master 1
2009-01-05 19:22:26.690 NVP: Enabling Audio
2009-01-05 19:22:26.692 AFD: Warning, audio codec 0x9a3bef0 id(AC3) type (Audio) already open, leaving it alone.
2009-01-05 19:22:26.693 AFD: codec AC3 has 2 channels
2009-01-05 19:22:46.566 DPMS Reactivated.
2009-01-05 19:22:47.895 AFD: Warning, video codec 0x8a98850 id(MPEG2VIDEO) type (Video) already open.
2009-01-05 19:22:47.980 DPMS Deactivated 
2009-01-05 19:22:48.192 AFD: Opened codec 0x867c160, id(DVD_SUBTITLE) type(Subtitle)
2009-01-05 19:22:48.192 NVP: Disabling Audio, params(-1,-1,-1)
2009-01-05 19:22:48.216 AFD: Warning, video codec 0x8a98850 id(MPEG2VIDEO) type (Video) already open.
2009-01-05 19:22:48.216 AFD: Opened codec 0x9a3c270, id(DVD_SUBTITLE) type(Subtitle)
2009-01-05 19:22:48.281 DPMS Reactivated.
2009-01-05 19:22:48.359 [mpeg2video @ 0xb73c4a88]00 motion_type at 1 1
2009-01-05 19:22:48.359 [mpeg2video @ 0xb73c4a88]00 motion_type at 1 2
2009-01-05 19:22:48.359 [mpeg2video @ 0xb73c4a88]00 motion_type at 11 3
2009-01-05 19:22:48.359 [mpeg2video @ 0xb73c4a88]00 motion_type at 6 4
2009-01-05 19:22:48.359 [mpeg2video @ 0xb73c4a88]00 motion_type at 1 5
2009-01-05 19:22:48.360 [mpeg2video @ 0xb73c4a88]00 motion_type at 4 6
2009-01-05 19:22:48.360 [mpeg2video @ 0xb73c4a88]00 motion_type at 1 7
2009-01-05 19:22:48.360 [mpeg2video @ 0xb73c4a88]invalid cbp at 0 8
2009-01-05 19:22:48.360 [mpeg2video @ 0xb73c4a88]invalid mb type in B Frame at 1 9
2009-01-05 19:22:48.360 [mpeg2video @ 0xb73c4a88]00 motion_type at 8 10
2009-01-05 19:22:48.360 [mpeg2video @ 0xb73c4a88]ac-tex damaged at 17 11
2009-01-05 19:22:48.361 [mpeg2video @ 0xb73c4a88]slice mismatch
2009-01-05 19:22:48.361 [mpeg2video @ 0xb73c4a88]00 motion_type at 5 13
2009-01-05 19:22:48.361 [mpeg2video @ 0xb73c4a88]00 motion_type at 8 14
2009-01-05 19:22:48.361 [mpeg2video @ 0xb73c4a88]ac-tex damaged at 10 15
2009-01-05 19:22:48.361 [mpeg2video @ 0xb73c4a88]00 motion_type at 1 16
2009-01-05 19:22:48.361 [mpeg2video @ 0xb73c4a88]00 motion_type at 1 17
2009-01-05 19:22:48.362 [mpeg2video @ 0xb73c4a88]00 motion_type at 1 18
2009-01-05 19:22:48.362 [mpeg2video @ 0xb73c4a88]00 motion_type at 7 19
2009-01-05 19:22:48.362 [mpeg2video @ 0xb73c4a88]ac-tex damaged at 14 20
2009-01-05 19:22:48.362 [mpeg2video @ 0xb73c4a88]ac-tex damaged at 23 21
2009-01-05 19:22:48.362 [mpeg2video @ 0xb73c4a88]invalid mb type in B Frame at 20 22
2009-01-05 19:22:48.363 [mpeg2video @ 0xb73c4a88]ac-tex damaged at 7 23
2009-01-05 19:22:48.363 [mpeg2video @ 0xb73c4a88]ac-tex damaged at 0 24
2009-01-05 19:22:48.363 [mpeg2video @ 0xb73c4a88]00 motion_type at 3 25
2009-01-05 19:22:48.363 [mpeg2video @ 0xb73c4a88]mb incr damaged
2009-01-05 19:22:48.363 [mpeg2video @ 0xb73c4a88]mb incr damaged
2009-01-05 19:22:48.363 [mpeg2video @ 0xb73c4a88]invalid cbp at 0 28
2009-01-05 19:22:48.364 [mpeg2video @ 0xb73c4a88]00 motion_type at 18 29
2009-01-05 19:22:48.364 [mpeg2video @ 0xb73c4a88]00 motion_type at 1 30
2009-01-05 19:22:48.364 [mpeg2video @ 0xb73c4a88]slice mismatch
2009-01-05 19:22:48.364 [mpeg2video @ 0xb73c4a88]00 motion_type at 28 32
2009-01-05 19:22:48.364 [mpeg2video @ 0xb73c4a88]invalid mb type in B Frame at 19 33
2009-01-05 19:22:48.364 [mpeg2video @ 0xb73c4a88]00 motion_type at 10 34
2009-01-05 19:22:48.365 [mpeg2video @ 0xb73c4a88]invalid cbp at 0 35
2009-01-05 19:22:48.365 [mpeg2video @ 0xb73c4a88]Warning MVs not available
2009-01-05 19:22:48.369 [mpeg2video @ 0xb73c4a88]00 motion_type at 1 1
2009-01-05 19:22:48.369 [mpeg2video @ 0xb73c4a88]00 motion_type at 1 2
2009-01-05 19:22:48.369 [mpeg2video @ 0xb73c4a88]00 motion_type at 11 3
2009-01-05 19:22:48.369 [mpeg2video @ 0xb73c4a88]00 motion_type at 6 4
2009-01-05 19:22:48.370 [mpeg2video @ 0xb73c4a88]00 motion_type at 1 5
2009-01-05 19:22:48.370 [mpeg2video @ 0xb73c4a88]00 motion_type at 4 6
2009-01-05 19:22:48.370 [mpeg2video @ 0xb73c4a88]00 motion_type at 1 7
2009-01-05 19:22:48.370 [mpeg2video @ 0xb73c4a88]invalid cbp at 0 8
2009-01-05 19:22:48.370 [mpeg2video @ 0xb73c4a88]invalid mb type in B Frame at 1 9
2009-01-05 19:22:48.370 [mpeg2video @ 0xb73c4a88]00 motion_type at 8 10
2009-01-05 19:22:48.371 [mpeg2video @ 0xb73c4a88]ac-tex damaged at 17 11
2009-01-05 19:22:48.371 [mpeg2video @ 0xb73c4a88]slice mismatch
2009-01-05 19:22:48.371 [mpeg2video @ 0xb73c4a88]00 motion_type at 5 13
2009-01-05 19:22:48.371 [mpeg2video @ 0xb73c4a88]00 motion_type at 8 14
2009-01-05 19:22:48.371 [mpeg2video @ 0xb73c4a88]ac-tex damaged at 10 15
2009-01-05 19:22:48.371 [mpeg2video @ 0xb73c4a88]00 motion_type at 1 16
2009-01-05 19:22:48.372 [mpeg2video @ 0xb73c4a88]00 motion_type at 1 17
2009-01-05 19:22:48.372 [mpeg2video @ 0xb73c4a88]00 motion_type at 1 18
2009-01-05 19:22:48.372 [mpeg2video @ 0xb73c4a88]00 motion_type at 7 19
2009-01-05 19:22:48.372 [mpeg2video @ 0xb73c4a88]ac-tex damaged at 14 20
2009-01-05 19:22:48.372 [mpeg2video @ 0xb73c4a88]ac-tex damaged at 23 21
2009-01-05 19:22:48.373 [mpeg2video @ 0xb73c4a88]invalid mb type in B Frame at 20 22
2009-01-05 19:22:48.373 [mpeg2video @ 0xb73c4a88]ac-tex damaged at 7 23
2009-01-05 19:22:48.373 [mpeg2video @ 0xb73c4a88]ac-tex damaged at 0 24
2009-01-05 19:22:48.373 [mpeg2video @ 0xb73c4a88]00 motion_type at 3 25
2009-01-05 19:22:48.373 [mpeg2video @ 0xb73c4a88]mb incr damaged
2009-01-05 19:22:48.374 [mpeg2video @ 0xb73c4a88]mb incr damaged
2009-01-05 19:22:48.374 [mpeg2video @ 0xb73c4a88]invalid cbp at 0 28
2009-01-05 19:22:48.374 [mpeg2video @ 0xb73c4a88]00 motion_type at 18 29
2009-01-05 19:22:48.374 [mpeg2video @ 0xb73c4a88]00 motion_type at 1 30
2009-01-05 19:22:48.374 [mpeg2video @ 0xb73c4a88]slice mismatch
2009-01-05 19:22:48.374 [mpeg2video @ 0xb73c4a88]00 motion_type at 28 32
2009-01-05 19:22:48.375 [mpeg2video @ 0xb73c4a88]invalid mb type in B Frame at 19 33
2009-01-05 19:22:48.375 [mpeg2video @ 0xb73c4a88]00 motion_type at 10 34
2009-01-05 19:22:48.375 [mpeg2video @ 0xb73c4a88]invalid cbp at 0 35


```

The movie may be suffering with the large amount of data logged to disc.
Any help?

thanks
jmig

---

### Post by murbanci on 2009-01-05
Here is the output of the log after changing the code for the drive:
```

2009-01-05 15:40:51.966 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-01-05 15:40:51.967 Using protocol version 40
2009-01-05 15:40:51.985 TV: Attempting to change from None to WatchingPreRecorded
libdvdread: Using libdvdcss version 1.2.10 for DVD access

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x000001e0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00021f20
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0004b0b3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x002335c0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x002335e0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x002d4d00
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002d4d20
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x002d8920
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x002d8940
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x002f4800
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x002f4820
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x002f5de0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x002f5e00
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x002ff520
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x002ff540
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x00309c00
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x00309c20
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x0030ffa0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x0030ffc0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x0031a280
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x0031a2a0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_0.VOB at 0x0031f6e0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x0031f7a0
libdvdread: Elapsed time 0
libdvdread: Found 11 VTS's
libdvdread: Elapsed time 0
libdvdnav: Using dvdnav version 0.1.10-xine from http://xine.sf.net
libdvdnav: DVD Title: DVD_VIDEO
libdvdnav: DVD Serial Number: 2D338477
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/murbancic/.dvdnav/DVD VIDEO.map'
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8
2009-01-05 15:40:52.307 Opened DVD device at /dev/dvd1
libdvdnav: Suspected RCE Region Protection!!!
2009-01-05 15:40:52.307 There are 24 titles on the disk
2009-01-05 15:40:52.307 Title 0 has 0 parts.
2009-01-05 15:40:52.307 Title 1 has 28 parts.
2009-01-05 15:40:52.307 Title 2 has 2 parts.
2009-01-05 15:40:52.307 Title 3 has 2 parts.
2009-01-05 15:40:52.307 Title 4 has 2 parts.
2009-01-05 15:40:52.307 Title 5 has 2 parts.
2009-01-05 15:40:52.307 Title 6 has 2 parts.
2009-01-05 15:40:52.307 Title 7 has 2 parts.
2009-01-05 15:40:52.307 Title 8 has 2 parts.
2009-01-05 15:40:52.307 Title 9 has 2 parts.
2009-01-05 15:40:52.307 Title 10 has 2 parts.
2009-01-05 15:40:52.307 Title 11 has 2 parts.
2009-01-05 15:40:52.307 Title 12 has 2 parts.
2009-01-05 15:40:52.308 Title 13 has 2 parts.
2009-01-05 15:40:52.308 Title 14 has 2 parts.
2009-01-05 15:40:52.308 Title 15 has 2 parts.
2009-01-05 15:40:52.308 Title 16 has 2 parts.
2009-01-05 15:40:52.308 Title 17 has 2 parts.
2009-01-05 15:40:52.308 Title 18 has 2 parts.
2009-01-05 15:40:52.308 Title 19 has 2 parts.
2009-01-05 15:40:52.308 Title 20 has 2 parts.
2009-01-05 15:40:52.308 Title 21 has 2 parts.
2009-01-05 15:40:52.308 Title 22 has 2 parts.
2009-01-05 15:40:52.308 Title 23 has 2 parts.
2009-01-05 15:40:52.321 DPMS Deactivated 
2009-01-05 15:40:52.426 AFD: Opened codec 0x9a90a20, id(MPEG2VIDEO) type(Video)
2009-01-05 15:40:52.426 NVP: Disabling Audio, params(-1,-1,-1)
2009-01-05 15:40:52.463 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-01-05 15:40:52.506 OSD Theme Dimensions W: 640 H: 480
2009-01-05 15:40:52.958 TV: Changing from None to WatchingPreRecorded
2009-01-05 15:40:53.063 Video timing method: USleep with busy wait
2009-01-05 15:40:53.152 AFD: Warning, video codec 0x9a90a20 id(MPEG2VIDEO) type (Video) already open.
2009-01-05 15:40:53.285 AFD: codec AC3 has 0 channels
2009-01-05 15:40:53.299 AFD: Opened codec 0xb26a67a0, id(AC3) type(Audio)
2009-01-05 15:40:53.303 Opening audio device 'default'. ch 2(2) sr 48000
2009-01-05 15:40:53.304 Opening ALSA audio device 'default'.
2009-01-05 15:40:53.403 mixer unable to find control Master 1
2009-01-05 15:40:53.404 NVP: Enabling Audio
2009-01-05 15:40:53.404 AFD: Warning, audio codec 0xb26a67a0 id(AC3) type (Audio) already open, leaving it alone.
2009-01-05 15:40:53.404 AFD: codec AC3 has 2 channels
libdvdnav: Suspected RCE Region Protection!!!

```

After pressing play from the menu:
```

2009-01-05 15:41:26.819 AFD: Warning, video codec 0x9a90a20 id(MPEG2VIDEO) type (Video) already open.
2009-01-05 15:41:26.826 AFD: Opened codec 0xb00b68f0, id(DVD_SUBTITLE) type(Subtitle)
2009-01-05 15:41:26.826 NVP: Disabling Audio, params(-1,-1,-1)
2009-01-05 15:41:26.833 AFD: Warning, video codec 0x9a90a20 id(MPEG2VIDEO) type (Video) already open.
2009-01-05 15:41:26.833 AFD: Opened codec 0xa8fcff10, id(DVD_SUBTITLE) type(Subtitle)
2009-01-05 15:41:26.837 AFD: Warning, video codec 0x9a90a20 id(MPEG2VIDEO) type (Video) already open.
2009-01-05 15:41:26.837 AFD: codec AC3 has 0 channels
2009-01-05 15:41:26.838 AFD: Opened codec 0xa8d3ef50, id(AC3) type(Audio)
2009-01-05 15:41:26.859 Opening audio device 'default'. ch 2(2) sr 48000
2009-01-05 15:41:26.859 Opening ALSA audio device 'default'.
2009-01-05 15:41:26.901 mixer unable to find control Master 1
2009-01-05 15:41:26.901 NVP: Enabling Audio
2009-01-05 15:41:26.901 [mpeg2video @ 0xb74c2764]00 motion_type at 32 7
2009-01-05 15:41:26.901 [mpeg2video @ 0xb74c2764]00 motion_type at 2 8
2009-01-05 15:41:26.901 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 9
2009-01-05 15:41:26.901 [mpeg2video @ 0xb74c2764]00 motion_type at 15 10
2009-01-05 15:41:26.901 [mpeg2video @ 0xb74c2764]00 motion_type at 4 11
2009-01-05 15:41:26.902 [mpeg2video @ 0xb74c2764]ac-tex damaged at 10 12
2009-01-05 15:41:26.902 [mpeg2video @ 0xb74c2764]00 motion_type at 9 13
2009-01-05 15:41:26.902 [mpeg2video @ 0xb74c2764]00 motion_type at 15 14
2009-01-05 15:41:26.902 [mpeg2video @ 0xb74c2764]00 motion_type at 4 15
2009-01-05 15:41:26.902 [mpeg2video @ 0xb74c2764]invalid cbp at 9 16
2009-01-05 15:41:26.902 [mpeg2video @ 0xb74c2764]mb incr damaged
2009-01-05 15:41:26.902 [mpeg2video @ 0xb74c2764]00 motion_type at 17 19
2009-01-05 15:41:26.902 [mpeg2video @ 0xb74c2764]ac-tex damaged at 9 20
2009-01-05 15:41:26.902 [mpeg2video @ 0xb74c2764]invalid mb type in P Frame at 3 21
2009-01-05 15:41:26.902 [mpeg2video @ 0xb74c2764]ac-tex damaged at 23 22
2009-01-05 15:41:26.902 [mpeg2video @ 0xb74c2764]00 motion_type at 14 23
2009-01-05 15:41:26.902 [mpeg2video @ 0xb74c2764]00 motion_type at 4 24
2009-01-05 15:41:26.902 [mpeg2video @ 0xb74c2764]00 motion_type at 4 25
2009-01-05 15:41:26.903 [mpeg2video @ 0xb74c2764]00 motion_type at 3 26
2009-01-05 15:41:26.903 [mpeg2video @ 0xb74c2764]00 motion_type at 25 27
2009-01-05 15:41:26.903 [mpeg2video @ 0xb74c2764]ac-tex damaged at 8 28
2009-01-05 15:41:26.903 [mpeg2video @ 0xb74c2764]invalid mb type in P Frame at 3 29
2009-01-05 15:41:26.903 [mpeg2video @ 0xb74c2764]Warning MVs not available
2009-01-05 15:41:56.673 WriteAudio: buffer underrun
2009-01-05 15:42:26.638 [ac3 @ 0xb74c2764]frame CRC mismatch
2009-01-05 15:42:36.987 [ac3 @ 0xb74c2764]frame CRC mismatch
2009-01-05 15:42:36.988 [mpeg2video @ 0xb74c2764]ac-tex damaged at 32 0
2009-01-05 15:42:36.988 [mpeg2video @ 0xb74c2764]Warning MVs not available
2009-01-05 15:42:37.168 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-05 15:42:37.172 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-05 15:42:37.176 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-05 15:42:37.180 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-05 15:42:37.184 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
libdvdnav: Suspected RCE Region Protection!!!
2009-01-05 15:42:40.903 [ac3 @ 0xb74c2764]frame CRC mismatch
libdvdnav: Suspected RCE Region Protection!!!
libdvdnav: Suspected RCE Region Protection!!!
2009-01-05 15:43:06.026 AFD: Warning, video codec 0x9a90a20 id(MPEG2VIDEO) type (Video) already open.
2009-01-05 15:43:06.026 NVP: Disabling Audio, params(-1,-1,-1)
2009-01-05 15:43:06.032 AFD: Warning, video codec 0x9a90a20 id(MPEG2VIDEO) type (Video) already open.
2009-01-05 15:43:06.033 AFD: codec AC3 has 0 channels
2009-01-05 15:43:06.033 AFD: Opened codec 0xa8cdc410, id(AC3) type(Audio)
2009-01-05 15:43:06.037 AFD: Warning, video codec 0x9a90a20 id(MPEG2VIDEO) type (Video) already open.
2009-01-05 15:43:06.037 AFD: Warning, audio codec 0xa8cdc410 id(AC3) type (Audio) already open, leaving it alone.
2009-01-05 15:43:06.037 AFD: codec AC3 has 6 channels
2009-01-05 15:43:06.037 AFD: codec AC3 has 0 channels
2009-01-05 15:43:06.038 AFD: Opened codec 0xa8cba510, id(AC3) type(Audio)
2009-01-05 15:43:06.038 NVP: Disabling Audio, params(0,0,0)
2009-01-05 15:43:06.041 Opening audio device 'default'. ch 2(2) sr 48000
2009-01-05 15:43:06.041 Opening ALSA audio device 'default'.
2009-01-05 15:43:06.084 mixer unable to find control Master 1
2009-01-05 15:43:06.085 NVP: Enabling Audio
2009-01-05 15:43:06.085 [ac3 @ 0xb74c2764]frame CRC mismatch
2009-01-05 15:43:06.089 AFD: Warning, video codec 0x9a90a20 id(MPEG2VIDEO) type (Video) already open.
2009-01-05 15:43:06.089 AFD: Warning, audio codec 0xa8cdc410 id(AC3) type (Audio) already open, leaving it alone.
2009-01-05 15:43:06.089 AFD: codec AC3 has 6 channels
2009-01-05 15:43:06.089 AFD: Warning, audio codec 0xa8cba510 id(AC3) type (Audio) already open, leaving it alone.
2009-01-05 15:43:06.089 AFD: codec AC3 has 2 channels
2009-01-05 15:43:06.089 AFD: codec AC3 has 0 channels
2009-01-05 15:43:06.090 AFD: Opened codec 0xa8d7edf0, id(AC3) type(Audio)
2009-01-05 15:43:06.120 NVP: prebuffering pause
2009-01-05 15:43:06.264 AFD: Warning, audio codec 0xa8cdc410 id(AC3) type (Audio) already open, leaving it alone.
2009-01-05 15:43:06.264 AFD: codec AC3 has 6 channels
2009-01-05 15:43:06.264 AFD: Warning, audio codec 0xa8cba510 id(AC3) type (Audio) already open, leaving it alone.
2009-01-05 15:43:06.264 AFD: codec AC3 has 2 channels
2009-01-05 15:43:06.264 AFD: Warning, audio codec 0xa8d7edf0 id(AC3) type (Audio) already open, leaving it alone.
2009-01-05 15:43:06.264 AFD: codec AC3 has 2 channels
2009-01-05 15:43:06.426 [mpeg2video @ 0xb74c2764]mb incr damaged
2009-01-05 15:43:06.426 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 8
2009-01-05 15:43:06.426 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 9
2009-01-05 15:43:06.427 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 10
2009-01-05 15:43:06.427 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 11
2009-01-05 15:43:06.427 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 12
2009-01-05 15:43:06.427 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 13
2009-01-05 15:43:06.427 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 14
2009-01-05 15:43:06.427 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 15
2009-01-05 15:43:06.427 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 16
2009-01-05 15:43:06.427 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 17
2009-01-05 15:43:06.427 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 18
2009-01-05 15:43:06.427 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 19
2009-01-05 15:43:06.427 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 20
2009-01-05 15:43:06.427 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 21
2009-01-05 15:43:06.427 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 22
2009-01-05 15:43:06.427 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 23
2009-01-05 15:43:06.427 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 24
2009-01-05 15:43:06.427 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 25
2009-01-05 15:43:06.427 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 26
2009-01-05 15:43:06.428 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 27
2009-01-05 15:43:06.428 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 28
2009-01-05 15:43:06.428 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 29
2009-01-05 15:43:06.428 [mpeg2video @ 0xb74c2764]Warning MVs not available
2009-01-05 15:43:06.433 [mpeg2video @ 0xb74c2764]sequence header damaged
2009-01-05 15:43:06.433 [mpeg2video @ 0xb74c2764]slice mismatch
2009-01-05 15:43:06.433 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 8
2009-01-05 15:43:06.433 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 9
2009-01-05 15:43:06.433 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 10
2009-01-05 15:43:06.433 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 11
2009-01-05 15:43:06.433 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 12
2009-01-05 15:43:06.433 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 13
2009-01-05 15:43:06.433 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 14
2009-01-05 15:43:06.433 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 15
2009-01-05 15:43:06.434 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 16
2009-01-05 15:43:06.434 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 17
2009-01-05 15:43:06.434 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 18
2009-01-05 15:43:06.434 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 19
2009-01-05 15:43:06.434 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 20
2009-01-05 15:43:06.434 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 21
2009-01-05 15:43:06.434 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 22
2009-01-05 15:43:06.434 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 23
2009-01-05 15:43:06.434 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 24
2009-01-05 15:43:06.434 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 25
2009-01-05 15:43:06.434 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 26
2009-01-05 15:43:06.434 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 27
2009-01-05 15:43:06.434 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 28
2009-01-05 15:43:06.434 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 29
2009-01-05 15:43:06.439 [mpeg2video @ 0xb74c2764]sequence header damaged
2009-01-05 15:43:06.439 [mpeg2video @ 0xb74c2764]slice mismatch
2009-01-05 15:43:06.439 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 8
2009-01-05 15:43:06.439 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 9
2009-01-05 15:43:06.440 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 10
2009-01-05 15:43:06.440 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 11
2009-01-05 15:43:06.440 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 12
2009-01-05 15:43:06.440 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 13
2009-01-05 15:43:06.440 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 14
2009-01-05 15:43:06.440 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 15
2009-01-05 15:43:06.440 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 16
2009-01-05 15:43:06.440 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 17
2009-01-05 15:43:06.440 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 18
2009-01-05 15:43:06.440 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 19
2009-01-05 15:43:06.440 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 20
2009-01-05 15:43:06.440 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 21
2009-01-05 15:43:06.440 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 22
2009-01-05 15:43:06.440 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 23
2009-01-05 15:43:06.440 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 24
2009-01-05 15:43:06.440 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 25
2009-01-05 15:43:06.440 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 26
2009-01-05 15:43:06.441 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 27
2009-01-05 15:43:06.441 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 28
2009-01-05 15:43:06.441 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 29
2009-01-05 15:43:06.445 [mpeg2video @ 0xb74c2764]sequence header damaged
2009-01-05 15:43:06.446 [mpeg2video @ 0xb74c2764]slice mismatch
2009-01-05 15:43:06.446 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 8
2009-01-05 15:43:06.446 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 9
2009-01-05 15:43:06.446 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 10
2009-01-05 15:43:06.446 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 11
2009-01-05 15:43:06.446 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 12
2009-01-05 15:43:06.446 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 13
2009-01-05 15:43:06.446 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 14
2009-01-05 15:43:06.446 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 15
2009-01-05 15:43:06.446 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 16
2009-01-05 15:43:06.446 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 17
2009-01-05 15:43:06.446 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 18
2009-01-05 15:43:06.446 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 19
2009-01-05 15:43:06.447 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 20
2009-01-05 15:43:06.447 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 21
2009-01-05 15:43:06.447 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 22
2009-01-05 15:43:06.447 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 23
2009-01-05 15:43:06.447 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 24
2009-01-05 15:43:06.447 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 25
2009-01-05 15:43:06.447 [mpeg2video @ 0xb74c2764]ac-tex damaged at 1 26
2009-01-05 15:43:06.447 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 27
2009-01-05 15:43:06.447 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 28
2009-01-05 15:43:06.447 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 29
2009-01-05 15:43:06.451 [ac3 @ 0xb74c2764]frame CRC mismatch
2009-01-05 15:43:06.457 [mpeg2video @ 0xb74c2764]sequence header damaged
2009-01-05 15:43:06.469 [ac3 @ 0xb74c2764]frame CRC mismatch
2009-01-05 15:43:06.475 [mpeg2video @ 0xb74c2764]sequence header damaged
2009-01-05 15:43:06.476 [mpeg2video @ 0xb74c2764]mb incr damaged
2009-01-05 15:43:06.476 [mpeg2video @ 0xb74c2764]ac-tex damaged at 3 15
2009-01-05 15:43:06.476 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 16
2009-01-05 15:43:06.476 [mpeg2video @ 0xb74c2764]00 motion_type at 5 17
2009-01-05 15:43:06.476 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 18
2009-01-05 15:43:06.476 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 19
2009-01-05 15:43:06.476 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 20
2009-01-05 15:43:06.476 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 21
2009-01-05 15:43:06.476 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 22
2009-01-05 15:43:06.476 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 23
2009-01-05 15:43:06.477 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 24
2009-01-05 15:43:06.477 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 25
2009-01-05 15:43:06.477 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 26
2009-01-05 15:43:06.477 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 27
2009-01-05 15:43:06.477 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 28
2009-01-05 15:43:06.477 [mpeg2video @ 0xb74c2764]ac-tex damaged at 0 29
2009-01-05 15:43:06.581 [ac3 @ 0xb74c2764]frame CRC mismatch
2009-01-05 15:43:06.587 [mpeg2video @ 0xb74c2764]sequence header damaged
2009-01-05 15:43:06.587 [mpeg2video @ 0xb74c2764]ac-tex damaged at 10 10
2009-01-05 15:43:06.587 [mpeg2video @ 0xb74c2764]slice mismatch
2009-01-05 15:43:06.587 [mpeg2video @ 0xb74c2764]slice mismatch
2009-01-05 15:43:06.587 [mpeg2video @ 0xb74c2764]invalid mb type in B Frame at 27 3
2009-01-05 15:43:06.587 [mpeg2video @ 0xb74c2764]ac-tex damaged at 24 7
2009-01-05 15:43:06.587 [mpeg2video @ 0xb74c2764]slice mismatch
2009-01-05 15:43:06.588 [mpeg2video @ 0xb74c2764]invalid cbp at 39 9
2009-01-05 15:43:06.588 [mpeg2video @ 0xb74c2764]invalid mb type in B Frame at 27 13
2009-01-05 15:43:06.588 [mpeg2video @ 0xb74c2764]invalid mb type in B Frame at 6 14
2009-01-05 15:43:06.588 [mpeg2video @ 0xb74c2764]invalid mb type in B Frame at 30 14
2009-01-05 15:43:06.588 [mpeg2video @ 0xb74c2764]slice mismatch
2009-01-05 15:43:06.588 [mpeg2video @ 0xb74c2764]ac-tex damaged at 20 20
2009-01-05 15:43:06.588 [mpeg2video @ 0xb74c2764]mb incr damaged
2009-01-05 15:43:06.588 [mpeg2video @ 0xb74c2764]slice mismatch
2009-01-05 15:43:06.588 [mpeg2video @ 0xb74c2764]ac-tex damaged at 19 26
2009-01-05 15:43:06.589 [mpeg2video @ 0xb74c2764]mb incr damaged
2009-01-05 15:43:06.592 [mpeg2video @ 0xb74c2764]ac-tex damaged at 12 2
2009-01-05 15:43:06.593 [mpeg2video @ 0xb74c2764]ac-tex damaged at 35 7
2009-01-05 15:43:06.593 [mpeg2video @ 0xb74c2764]mb incr damaged
2009-01-05 15:43:06.593 [mpeg2video @ 0xb74c2764]ac-tex damaged at 38 18
2009-01-05 15:43:06.594 [mpeg2video @ 0xb74c2764]ac-tex damaged at 30 24
2009-01-05 15:43:06.594 [mpeg2video @ 0xb74c2764]end mismatch left=428011 773230

```

At the bottom of the first block it says "libdvdnav: Suspected RCE Region Protection!!!".  I think it is just unable to crack the encryption on the disk :(

---

