---
title: "What's the best way to join two .trp video files?"
date: 2009-10-02
forum: Multimedia Software
---

### Post by rob86 on 2009-10-02
I've been trying to find an easy command line way to join my trp video files into one (Movie.trp,Movie.001,Movie.002). I have all the tools (I think), ffmpeg, mencoder, and the humble cat command. 

I had some success converting my files to mpeg2 or whatever it was, then "cat"ing them, then re-encoding them, but that seems like a long round about way to do things. Isn't there any easier way to join these files? 

I tried this command (filling in my filenames ofcourse) 

```
mencoder -oac copy -ovc copy -o [whole] [part1] [part2] ... [partn]
```

but unfortunately, for some reason it didn't quite work. The videos almost joined, and the combined length correctly is shown in smplayer, but 
it only encoded about 7 seconds, after that the video stops. I wonder if it's because it's an .trp file and not an .avi. There's a warning there.. I don't know

Here's the output, it's long and I don't understand much of it, so I don't know how helpful it will be to paste it.

By the way, unrelated question but, what's with all the duplicate frames? It really clutters up the output, I get that even on successful encodes.

```
WARNING: OUTPUT FILE FORMAT IS _AVI_. See -of help.
success: format: 0  data: 0x0 - 0x2630000
TS file format detected.
VIDEO MPEG2(pid=7202) AUDIO MPA(pid=7203) NO SUBS (yet)!  PROGRAM N. 0
VIDEO:  MPEG2  544x480  (aspect 2)  29.970 fps  15000.0 kbps (1875.0 kbyte/s)
[V] filefmt:29  fourcc:0x10000002  size:544x480  fps:29.97  ftime:=0.0334
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 160.0 kbit/10.42% (ratio: 20000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
videocodec: framecopy (544x480 24bpp fourcc=10000002)
audiocodec: framecopy (format=50 chans=2 rate=48000 bits=16 B/s=20000 sample-1)
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Pos:   0.5s     16f ( 1%)  0.00fps Trem:   0min  21mb  A-V:-0.050 [0:160]
1 duplicate frame(s)!
Pos:   0.7s     21f ( 1%)  0.00fps Trem:   0min  25mb  A-V:-0.067 [0:160]
1 duplicate frame(s)!
Pos:   0.8s     22f ( 1%)  0.00fps Trem:   0min  27mb  A-V:-0.070 [0:160]
demux_mpg: 24000/1001fps progressive NTSC content detected, switching framerate.

2 duplicate frame(s)!
Pos:   1.0s     25f ( 1%)  0.00fps Trem:   0min  29mb  A-V:-0.048 [0:160]
1 duplicate frame(s)!
Pos:   1.1s     29f ( 1%)  0.00fps Trem:   0min  24mb  A-V:-0.065 [2475:160]
1 duplicate frame(s)!
Pos:   1.2s     30f ( 1%)  0.00fps Trem:   0min  24mb  A-V:-0.069 [2385:160]
1 duplicate frame(s)!
Pos:   1.3s     33f ( 1%)  0.00fps Trem:   0min  26mb  A-V:-0.048 [2338:160]
1 duplicate frame(s)!
Pos:   1.5s     37f ( 1%)  0.00fps Trem:   0min  29mb  A-V:-0.065 [2339:160]
1 duplicate frame(s)!
Pos:   1.6s     38f ( 1%)  0.00fps Trem:   0min  25mb  A-V:-0.069 [2274:160]
1 duplicate frame(s)!
Pos:   1.7s     41f ( 1%)  0.00fps Trem:   0min  27mb  A-V:-0.048 [2243:160]
1 duplicate frame(s)!
Pos:   1.9s     45f ( 1%)  0.00fps Trem:   0min  29mb  A-V:-0.065 [2227:160]
1 duplicate frame(s)!
Pos:   1.9s     46f ( 1%)  0.00fps Trem:   0min  30mb  A-V:-0.069 [2204:160]
1 duplicate frame(s)!
Pos:   2.1s     49f ( 2%)  0.00fps Trem:   0min  28mb  A-V:-0.048 [2198:160]
1 duplicate frame(s)!
Pos:   2.2s     53f ( 2%)  0.00fps Trem:   0min  30mb  A-V:-0.065 [2251:160]
1 duplicate frame(s)!
Pos:   2.3s     54f ( 2%)  0.00fps Trem:   0min  31mb  A-V:-0.069 [2221:160]
1 duplicate frame(s)!
Pos:   2.4s     57f ( 2%)  0.00fps Trem:   0min  32mb  A-V:-0.048 [2198:160]
1 duplicate frame(s)!
Pos:   2.6s     61f ( 2%)  0.00fps Trem:   0min  29mb  A-V:-0.065 [2194:160]
1 duplicate frame(s)!
Pos:   2.7s     62f ( 2%)  0.00fps Trem:   0min  30mb  A-V:-0.069 [2161:160]
1 duplicate frame(s)!
Pos:   2.8s     65f ( 2%)  0.00fps Trem:   0min  31mb  A-V:-0.048 [2154:160]
1 duplicate frame(s)!
Pos:   3.0s     69f ( 2%)  0.00fps Trem:   0min  33mb  A-V:-0.065 [2180:160]
1 duplicate frame(s)!
Pos:   3.0s     70f ( 2%)  0.00fps Trem:   0min  33mb  A-V:-0.069 [2155:160]
1 duplicate frame(s)!
Pos:   3.2s     73f ( 2%)  0.00fps Trem:   0min  31mb  A-V:-0.048 [2113:160]
demux_mpg: 30000/1001fps NTSC content detected, switching framerate.

1 duplicate frame(s)!
Warning! FPS changed 23.976 -> 29.970  (-5.994005) [4]  -V:-0.053 [2079:160]
Pos:   3.4s     79f ( 2%)  0.00fps Trem:   0min  32mb  A-V:-0.070 [2045:160]
1 duplicate frame(s)!
Pos:   3.7s     88f ( 3%)  0.00fps Trem:   0min  31mb  A-V:-0.067 [1976:160]
1 duplicate frame(s)!
Pos:   3.8s     89f ( 3%)  0.00fps Trem:   0min  31mb  A-V:-0.070 [1948:160]
1 duplicate frame(s)!
Pos:   4.0s     94f ( 3%)  0.00fps Trem:   0min  32mb  A-V:-0.053 [1908:160]
1 duplicate frame(s)!
Pos:   4.2s     99f ( 3%)  0.00fps Trem:   0min  31mb  A-V:-0.070 [1861:160]
1 duplicate frame(s)!
Pos:   4.6s    109f ( 3%)  0.00fps Trem:   0min  31mb  A-V:-0.070 [1818:160]
1 duplicate frame(s)!
Pos:   4.9s    119f ( 3%)  0.00fps Trem:   0min  32mb  A-V:-0.070 [1777:160]
1 duplicate frame(s)!
Pos:   5.3s    128f ( 3%)  0.00fps Trem:   0min  33mb  A-V:-0.067 [1762:160]
1 duplicate frame(s)!
Pos:   5.3s    129f ( 3%)  0.00fps Trem:   0min  33mb  A-V:-0.070 [1745:160]
1 duplicate frame(s)!
Pos:   5.4s    130f ( 3%)  0.00fps Trem:   0min  33mb  A-V:-0.040 [1735:160]
1 duplicate frame(s)!
Pos:   5.7s    139f ( 3%)  0.00fps Trem:   0min  32mb  A-V:-0.070 [1727:160]
1 duplicate frame(s)!
Pos:   6.1s    149f ( 4%)  0.00fps Trem:   0min  32mb  A-V:-0.070 [1697:160]
1 duplicate frame(s)!
Pos:   6.5s    159f ( 4%)  0.00fps Trem:   0min  33mb  A-V:-0.070 [1660:160]
1 duplicate frame(s)!
Pos:   6.8s    169f ( 4%)  0.00fps Trem:   0min  33mb  A-V:-0.070 [1618:160]
1 duplicate frame(s)!
Pos:   7.2s    179f ( 4%)  0.00fps Trem:   0min  33mb  A-V:-0.070 [1604:160]
1 duplicate frame(s)!
Pos:   7.6s    189f ( 4%)  0.00fps Trem:   0min  32mb  A-V:-0.070 [1573:160]
1 duplicate frame(s)!
Pos:   7.9s    199f ( 4%)  0.00fps Trem:   0min  33mb  A-V:-0.070 [1546:160]
1 duplicate frame(s)!
Pos:   8.3s    209f ( 5%)  0.00fps Trem:   0min  33mb  A-V:-0.070 [1521:160]
1 duplicate frame(s)!
Pos:   8.7s    219f ( 5%)  0.00fps Trem:   0min  32mb  A-V:-0.070 [1506:160]
1 duplicate frame(s)!
Pos:   9.0s    229f ( 5%)  0.00fps Trem:   0min  32mb  A-V:-0.070 [1475:160]
1 duplicate frame(s)!
Pos:   9.4s    239f ( 5%)  0.00fps Trem:   0min  33mb  A-V:-0.070 [1473:160]
1 duplicate frame(s)!
Pos:   9.8s    249f ( 5%)  0.00fps Trem:   0min  32mb  A-V:-0.070 [1462:160]
1 duplicate frame(s)!
Pos:  10.0s    256f ( 6%)  0.00fps Trem:   0min  32mb  A-V:-0.060 [1456:160]
1 duplicate frame(s)!
Pos:  10.2s    259f ( 6%)  0.00fps Trem:   0min  32mb  A-V:-0.069 [1449:160]
1 duplicate frame(s)!
Pos:  10.9s    279f ( 6%)  0.00fps Trem:   0min  32mb  A-V:-0.067 [1413:160]
1 duplicate frame(s)!
Pos:  13.2s    347f ( 7%)  0.00fps Trem:   0min  32mb  A-V:-0.031 [1408:160]
1 duplicate frame(s)!
Pos:  14.0s    370f ( 7%)  0.00fps Trem:   0min  33mb  A-V:-0.033 [1425:160]
1 duplicate frame(s)!
Pos:  14.1s    374f ( 8%)  0.00fps Trem:   0min  32mb  A-V:-0.028 [1426:160]
1 duplicate frame(s)!
Pos:  14.3s    378f ( 8%)  0.00fps Trem:   0min  32mb  A-V:-0.024 [1427:160]
1 duplicate frame(s)!
Pos:  14.4s    380f ( 8%)  0.00fps Trem:   0min  32mb  A-V:-0.023 [1425:160]
demux_mpg: 24000/1001fps progressive NTSC content detected, switching framerate.
Pos:  14.4s    381f ( 8%)  0.00fps Trem:   0min  33mb  A-V:-0.021 [1426:160]
1 duplicate frame(s)!
Pos:  14.6s    385f ( 8%)  0.00fps Trem:   0min  32mb  A-V:-0.015 [1425:160]
1 duplicate frame(s)!
Pos:  14.8s    389f ( 8%)  0.00fps Trem:   0min  33mb  A-V:-0.011 [1433:160]
1 duplicate frame(s)!
Pos:  14.9s    393f ( 8%)  0.00fps Trem:   0min  33mb  A-V:-0.009 [1431:160]
1 duplicate frame(s)!
Pos:  15.1s    397f ( 8%)  0.00fps Trem:   0min  32mb  A-V:-0.006 [1435:160]
1 duplicate frame(s)!
Pos:  15.3s    401f ( 8%)  0.00fps Trem:   0min  32mb  A-V:-0.005 [1433:160]
1 duplicate frame(s)!
Pos:  15.4s    405f ( 8%)  0.00fps Trem:   0min  33mb  A-V:-0.004 [1431:160]
1 duplicate frame(s)!
Pos:  15.6s    409f ( 9%)  0.00fps Trem:   0min  32mb  A-V:-0.004 [1437:160]
1 duplicate frame(s)!
Pos:  15.8s    413f ( 9%)  0.00fps Trem:   0min  33mb  A-V:-0.004 [1437:160]
1 duplicate frame(s)!
Pos:  15.9s    417f ( 9%)  0.00fps Trem:   0min  33mb  A-V:-0.005 [1438:160]
1 duplicate frame(s)!
Pos:  16.1s    421f ( 9%)  0.00fps Trem:   0min  33mb  A-V:-0.004 [1443:160]
1 duplicate frame(s)!
Pos:  16.3s    425f ( 9%)  0.00fps Trem:   0min  33mb  A-V:-0.003 [1443:160]
1 duplicate frame(s)!
Pos:  16.4s    429f ( 9%)  0.00fps Trem:   0min  33mb  A-V:-0.003 [1443:160]
1 duplicate frame(s)!
Pos:  16.6s    433f ( 9%)  0.00fps Trem:   0min  33mb  A-V:-0.003 [1457:160]
1 duplicate frame(s)!
Pos:  16.8s    437f ( 9%)  0.00fps Trem:   0min  33mb  A-V:-0.003 [1452:160]
1 duplicate frame(s)!
Pos:  17.0s    441f ( 9%)  0.00fps Trem:   0min  34mb  A-V:-0.004 [1448:160]
1 duplicate frame(s)!
Pos:  17.1s    445f ( 9%)  0.00fps Trem:   0min  33mb  A-V:-0.003 [1445:160]
1 duplicate frame(s)!
Pos:  17.3s    449f ( 9%)  0.00fps Trem:   0min  33mb  A-V:0.003 [1440:160]]
1 duplicate frame(s)!
Pos:  17.4s    452f ( 9%)  0.00fps Trem:   0min  33mb  A-V:0.015 [1437:160]
demux_mpg: 30000/1001fps NTSC content detected, switching framerate.
Warning! FPS changed 23.976 -> 29.970  (-5.994005) [4]  -V:0.019 [1435:160]
Pos:  18.6s    488f (10%)  0.00fps Trem:   0min  34mb  A-V:0.031 [1439:160]
1 duplicate frame(s)!
Pos:  30.7s    848f (16%)  0.00fps Trem:   0min  34mb  A-V:0.027 [1413:160]
1 duplicate frame(s)!
Pos:  30.8s    851f (16%)  0.00fps Trem:   0min  34mb  A-V:0.031 [1410:160]
1 duplicate frame(s)!
Pos:  31.1s    859f (17%)  0.00fps Trem:   0min  34mb  A-V:0.005 [1412:160]
demux_mpg: 24000/1001fps progressive NTSC content detected, switching framerate.

1 duplicate frame(s)!
Pos:  31.2s    860f (17%)  0.00fps Trem:   0min  34mb  A-V:0.007 [1412:160]
1 duplicate frame(s)!
Pos:  31.3s    864f (17%)  0.00fps Trem:   0min  34mb  A-V:0.014 [1414:160]
1 duplicate frame(s)!
Pos:  31.5s    868f (17%)  0.00fps Trem:   0min  34mb  A-V:0.018 [1416:160]
1 duplicate frame(s)!
Pos:  31.7s    872f (17%)  0.00fps Trem:   0min  34mb  A-V:0.021 [1418:160]
1 duplicate frame(s)!
Pos:  31.8s    876f (17%)  0.00fps Trem:   0min  34mb  A-V:0.022 [1428:160]
1 duplicate frame(s)!
Pos:  32.0s    880f (17%)  0.00fps Trem:   0min  35mb  A-V:0.023 [1439:160]
1 duplicate frame(s)!
Pos:  32.2s    884f (17%)  0.00fps Trem:   0min  34mb  A-V:0.025 [1449:160]
1 duplicate frame(s)!
Pos:  32.3s    888f (17%)  0.00fps Trem:   0min  34mb  A-V:0.026 [1451:160]
1 duplicate frame(s)!
Pos:  32.5s    892f (17%)  0.00fps Trem:   0min  35mb  A-V:0.026 [1454:160]
1 duplicate frame(s)!
Pos:  32.7s    896f (18%)  0.00fps Trem:   0min  34mb  A-V:0.026 [1455:160]
1 duplicate frame(s)!
Pos:  32.8s    900f (18%)  0.00fps Trem:   0min  34mb  A-V:0.026 [1458:160]
1 duplicate frame(s)!
Pos:  33.0s    904f (18%)  0.00fps Trem:   0min  35mb  A-V:0.026 [1461:160]
1 duplicate frame(s)!
Pos:  33.2s    908f (18%)  0.00fps Trem:   0min  34mb  A-V:0.027 [1468:160]
1 duplicate frame(s)!
Pos:  33.3s    912f (18%)  0.00fps Trem:   0min  35mb  A-V:0.027 [1471:160]
1 duplicate frame(s)!
Pos:  33.5s    916f (18%)  0.00fps Trem:   0min  35mb  A-V:0.027 [1478:160]
1 duplicate frame(s)!
Pos:  33.7s    920f (18%)  0.00fps Trem:   0min  35mb  A-V:0.026 [1480:160]
1 duplicate frame(s)!
Pos:  33.8s    924f (18%)  0.00fps Trem:   0min  35mb  A-V:0.026 [1480:160]
1 duplicate frame(s)!
Pos:  34.0s    928f (18%)  0.00fps Trem:   0min  35mb  A-V:0.025 [1479:160]
1 duplicate frame(s)!
Pos:  34.2s    932f (19%)  0.00fps Trem:   0min  34mb  A-V:0.026 [1479:160]
1 duplicate frame(s)!
Pos:  34.3s    936f (19%)  0.00fps Trem:   0min  34mb  A-V:0.026 [1478:160]
1 duplicate frame(s)!
Pos:  34.5s    940f (19%)  0.00fps Trem:   0min  35mb  A-V:0.026 [1477:160]
1 duplicate frame(s)!
Pos:  34.7s    944f (19%)  0.00fps Trem:   0min  34mb  A-V:0.026 [1479:160]
1 duplicate frame(s)!
Pos:  34.8s    948f (19%)  0.00fps Trem:   0min  34mb  A-V:0.025 [1483:160]
1 duplicate frame(s)!
Pos:  35.0s    952f (19%)  0.00fps Trem:   0min  35mb  A-V:0.031 [1487:160]
1 duplicate frame(s)!
Pos:  35.1s    955f (20%)  0.00fps Trem:   0min  34mb  A-V:0.043 [1489:160]
demux_mpg: 30000/1001fps NTSC content detected, switching framerate.
Warning! FPS changed 23.976 -> 29.970  (-5.994005) [4]  -V:0.047 [1491:160]
Pos:  35.4s    963f (20%)  0.00fps Trem:   0min  34mb  A-V:0.068 [1495:160]
Skipping frame!
Pos:  85.0s   2451f (55%)  0.00fps Trem:   0min  36mb  A-V:0.022 [1838:160]
1 duplicate frame(s)!
Pos:  85.2s   2456f (56%)  0.00fps Trem:   0min  36mb  A-V:0.030 [1841:160]
1 duplicate frame(s)!
Pos:  85.3s   2458f (56%)  0.00fps Trem:   0min  36mb  A-V:0.032 [1840:160]
1 duplicate frame(s)!
Pos:  85.5s   2463f (56%)  0.00fps Trem:   0min  36mb  A-V:0.035 [1838:160]
demux_mpg: 24000/1001fps progressive NTSC content detected, switching framerate.
Pos:  85.6s   2465f (56%)  0.00fps Trem:   0min  36mb  A-V:0.005 [1838:160]
1 duplicate frame(s)!
Pos:  85.8s   2469f (56%)  0.00fps Trem:   0min  36mb  A-V:0.011 [1837:160]
1 duplicate frame(s)!
Pos:  85.9s   2473f (56%)  0.00fps Trem:   0min  36mb  A-V:0.024 [1836:160]
demux_mpg: 30000/1001fps NTSC content detected, switching framerate.

1 duplicate frame(s)!
Warning! FPS changed 23.976 -> 29.970  (-5.994005) [4]  -V:0.028 [1835:160]
Pos:  87.1s   2507f (57%)  0.00fps Trem:   0min  36mb  A-V:0.067 [1840:160]
Skipping frame!
Pos: 124.1s   3618f (87%) 2787.36fps Trem:   0min  36mb  A-V:0.003 [1985:160]
1 duplicate frame(s)!
Pos: 124.3s   3623f (87%) 2789.07fps Trem:   0min  36mb  A-V:0.010 [1984:160]
1 duplicate frame(s)!
Pos: 144.9s   4240f (97%) 2839.92fps Trem:   0min  36mb  A-V:0.002 [1906:160]]
1 duplicate frame(s)!
Pos: 146.8s   4294f (99%) 2856.95fps Trem:   0min  36mb  A-V:0.003 [1908:160]
1 duplicate frame(s)!
TS_PARSE: COULDN'T SYNC%) 2865.21fps Trem:   0min  36mb  A-V:0.005 [1907:160]
success: format: 0  data: 0x0 - 0x2630000m:   0min  36mb  A-V:-0.002 [1907:160]
TS file format detected.
VIDEO MPEG2(pid=7202) AUDIO MPA(pid=7203) NO SUBS (yet)!  PROGRAM N. 0
VIDEO:  MPEG2  544x480  (aspect 2)  29.970 fps  15000.0 kbps (1875.0 kbyte/s)
[V] filefmt:29  fourcc:0x10000002  size:544x480  fps:29.97  ftime:=0.0334
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 160.0 kbit/10.42% (ratio: 20000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
videocodec: framecopy (544x480 24bpp fourcc=10000002)
audiocodec: framecopy (format=50 chans=2 rate=48000 bits=16 B/s=20000 sample-1)
Pos: 149.2s   4365f ( 1%) 1990.42fps Trem:   3min 3301mb  A-V:-0.045 [1911:160]
1 duplicate frame(s)!
Pos: 149.4s   4370f ( 1%) 1991.80fps Trem:   2min 2384mb  A-V:-0.062 [1912:160]
1 duplicate frame(s)!
Pos: 149.5s   4372f ( 1%) 1991.80fps Trem:   2min 2386mb  A-V:-0.069 [1912:160]
demux_mpg: 24000/1001fps progressive NTSC content detected, switching framerate.

2 duplicate frame(s)!
Pos: 149.6s   4374f ( 1%) 1992.71fps Trem:   2min 2386mb  A-V:-0.043 [1911:160]
1 duplicate frame(s)!
Pos: 149.8s   4378f ( 1%) 1993.62fps Trem:   2min 2389mb  A-V:-0.060 [1911:160]
1 duplicate frame(s)!
Pos: 149.9s   4380f ( 1%) 1994.54fps Trem:   1min 2011mb  A-V:-0.068 [1911:160]
1 duplicate frame(s)!
Pos: 150.0s   4382f ( 1%) 1994.54fps Trem:   1min 2012mb  A-V:-0.043 [1911:160]
1 duplicate frame(s)!
Pos: 150.2s   4386f ( 1%) 1996.36fps Trem:   1min 2014mb  A-V:-0.060 [1911:160]
1 duplicate frame(s)!
Pos: 150.3s   4388f ( 1%) 1996.36fps Trem:   1min 2015mb  A-V:-0.068 [1911:160]
1 duplicate frame(s)!
Pos: 150.4s   4390f ( 2%) 1996.36fps Trem:   1min 1728mb  A-V:-0.043 [1911:160]
1 duplicate frame(s)!
Pos: 150.5s   4394f ( 2%) 1995.46fps Trem:   1min 1730mb  A-V:-0.060 [1911:160]
1 duplicate frame(s)!
Pos: 150.6s   4396f ( 2%) 1996.37fps Trem:   1min 1731mb  A-V:-0.068 [1911:160]
1 duplicate frame(s)!
Pos: 150.7s   4398f ( 2%) 1996.37fps Trem:   1min 1732mb  A-V:-0.043 [1911:160]
1 duplicate frame(s)!
Pos: 150.9s   4402f ( 2%) 1997.28fps Trem:   1min 1478mb  A-V:-0.060 [1912:160]
1 duplicate frame(s)!
Pos: 151.0s   4404f ( 2%) 1998.19fps Trem:   1min 1479mb  A-V:-0.068 [1912:160]
1 duplicate frame(s)!
Pos: 151.1s   4406f ( 2%) 1998.19fps Trem:   1min 1480mb  A-V:-0.043 [1912:160]
1 duplicate frame(s)!
Pos: 151.3s   4410f ( 2%) 2000.00fps Trem:   1min 1481mb  A-V:-0.060 [1911:160]
1 duplicate frame(s)!
Pos: 151.4s   4412f ( 2%) 2000.00fps Trem:   1min 1325mb  A-V:-0.068 [1912:160]
1 duplicate frame(s)!
Pos: 151.5s   4414f ( 2%) 2000.00fps Trem:   1min 1326mb  A-V:-0.043 [1912:160]
1 duplicate frame(s)!
Pos: 151.6s   4418f ( 2%) 2000.91fps Trem:   1min 1328mb  A-V:-0.060 [1913:160]
1 duplicate frame(s)!
Pos: 151.7s   4420f ( 2%) 2001.81fps Trem:   1min 1329mb  A-V:-0.068 [1912:160]
1 duplicate frame(s)!
Pos: 151.8s   4422f ( 3%) 1850.98fps Trem:   1min 1208mb  A-V:-0.043 [1911:160]
1 duplicate frame(s)!
Pos: 151.9s   4423f ( 3%) 1851.40fps Trem:   1min 1209mb  A-V:-0.047 [1911:160]
demux_mpg: 30000/1001fps NTSC content detected, switching framerate.
Warning! FPS changed 23.976 -> 29.970  (-5.994005) [4]    A-V:-0.051 [1911:160]
Pos: 152.1s   4429f ( 3%) 1853.14fps Trem:   1min 1210mb  A-V:-0.069 [1910:160]
1 duplicate frame(s)!
Pos: 152.4s   4438f ( 3%) 1853.03fps Trem:   1min 1149mb  A-V:-0.065 [1909:160]
1 duplicate frame(s)!
Pos: 152.5s   4439f ( 3%) 1853.44fps Trem:   1min 1149mb  A-V:-0.069 [1908:160]
1 duplicate frame(s)!
Pos: 152.7s   4444f ( 3%) 1853.98fps Trem:   1min 1150mb  A-V:-0.052 [1907:160]
1 duplicate frame(s)!
Pos: 152.9s   4449f ( 3%) 1855.30fps Trem:   1min 1065mb  A-V:-0.069 [1906:160]
1 duplicate frame(s)!
Pos: 153.3s   4459f ( 3%) 1857.14fps Trem:   1min 1067mb  A-V:-0.069 [1904:160]
1 duplicate frame(s)!
Pos: 153.6s   4469f ( 3%) 1859.76fps Trem:   1min 1024mb  A-V:-0.069 [1903:160]
1 duplicate frame(s)!
Pos: 154.0s   4478f ( 3%) 1858.09fps Trem:   0min 953mb  A-V:-0.065 [1902:160]]
1 duplicate frame(s)!
Pos: 154.0s   4479f ( 3%) 1858.51fps Trem:   0min 953mb  A-V:-0.068 [1901:160]
1 duplicate frame(s)!
Pos: 154.1s   4480f ( 3%) 1858.92fps Trem:   0min 953mb  A-V:-0.037 [1901:160]
1 duplicate frame(s)!
Pos: 154.8s   4501f ( 4%) 1863.00fps Trem:   0min 859mb  A-V:-0.068 [1899:160]
1 duplicate frame(s)!
Pos: 158.4s   4606f ( 6%) 1876.94fps Trem:   0min 640mb  A-V:-0.041 [1883:160]
1 duplicate frame(s)!
Pos: 161.4s   4697f ( 7%) 1890.90fps Trem:   0min 508mb  A-V:-0.036 [1871:160]
1 duplicate frame(s)!
Pos: 162.2s   4720f ( 7%) 1891.78fps Trem:   0min 492mb  A-V:-0.038 [1871:160]
1 duplicate frame(s)!
Pos: 162.4s   4724f ( 8%) 1891.87fps Trem:   0min 472mb  A-V:-0.033 [1870:160]
1 duplicate frame(s)!
Pos: 162.6s   4728f ( 8%) 1892.71fps Trem:   0min 473mb  A-V:-0.029 [1870:160]
1 duplicate frame(s)!
Pos: 162.7s   4730f ( 8%) 1893.51fps Trem:   0min 473mb  A-V:-0.028 [1869:160]
demux_mpg: 24000/1001fps progressive NTSC content detected, switching framerate.

1 duplicate frame(s)!
Pos: 162.8s   4734f ( 8%) 1891.33fps Trem:   0min 461mb  A-V:-0.021 [1869:160]
1 duplicate frame(s)!
Pos: 163.0s   4738f ( 8%) 1892.17fps Trem:   0min 461mb  A-V:-0.017 [1869:160]
1 duplicate frame(s)!
Pos: 163.2s   4742f ( 8%) 1893.77fps Trem:   0min 461mb  A-V:-0.014 [1869:160]
1 duplicate frame(s)!
Pos: 163.3s   4746f ( 8%) 1890.08fps Trem:   0min 445mb  A-V:-0.011 [1868:160]
1 duplicate frame(s)!
Pos: 163.5s   4750f ( 8%) 1890.92fps Trem:   0min 445mb  A-V:-0.010 [1868:160]
1 duplicate frame(s)!
Pos: 163.7s   4754f ( 8%) 1892.52fps Trem:   0min 446mb  A-V:-0.009 [1867:160]
1 duplicate frame(s)!
Pos: 163.8s   4758f ( 9%) 1893.35fps Trem:   0min 435mb  A-V:-0.009 [1867:160]
1 duplicate frame(s)!
Pos: 164.0s   4762f ( 9%) 1894.19fps Trem:   0min 435mb  A-V:-0.009 [1867:160]
1 duplicate frame(s)!
Pos: 164.2s   4766f ( 9%) 1895.78fps Trem:   0min 436mb  A-V:-0.009 [1867:160]
1 duplicate frame(s)!
Pos: 164.3s   4770f ( 9%) 1895.11fps Trem:   0min 424mb  A-V:-0.009 [1866:160]
1 duplicate frame(s)!
Pos: 164.5s   4774f ( 9%) 1895.95fps Trem:   0min 424mb  A-V:-0.008 [1866:160]
1 duplicate frame(s)!
Pos: 164.7s   4778f ( 9%) 1897.54fps Trem:   0min 425mb  A-V:-0.008 [1866:160]
1 duplicate frame(s)!
Pos: 164.8s   4782f ( 9%) 1895.36fps Trem:   0min 416mb  A-V:-0.008 [1867:160]
1 duplicate frame(s)!
Pos: 165.0s   4786f ( 9%) 1896.20fps Trem:   0min 417mb  A-V:-0.008 [1866:160]
1 duplicate frame(s)!
Pos: 165.2s   4790f ( 9%) 1897.78fps Trem:   0min 417mb  A-V:-0.008 [1865:160]
1 duplicate frame(s)!
Pos: 165.3s   4794f ( 9%) 1894.86fps Trem:   0min 404mb  A-V:-0.008 [1864:160]
1 duplicate frame(s)!
Pos: 165.5s   4798f ( 9%) 1895.69fps Trem:   0min 404mb  A-V:-0.005 [1864:160]
1 duplicate frame(s)!
Pos: 165.7s   4802f ( 9%) 1896.52fps Trem:   0min 405mb  A-V:0.009 [1863:160]]
demux_mpg: 30000/1001fps NTSC content detected, switching framerate.

1 duplicate frame(s)!
Warning! FPS changed 23.976 -> 29.970  (-5.994005) [4]   A-V:0.014 [1862:160]
Pos: 167.0s   4840f (10%) 1904.01fps Trem:   0min 384mb  A-V:0.026 [1859:160]
1 duplicate frame(s)!
Pos: 179.0s   5199f (16%) 1948.65fps Trem:   0min 255mb  A-V:0.023 [1826:160]
1 duplicate frame(s)!
Pos: 179.1s   5203f (16%) 1950.15fps Trem:   0min 255mb  A-V:0.028 [1826:160]
1 duplicate frame(s)!
Pos: 179.3s   5207f (17%) 1942.91fps Trem:   0min 248mb  A-V:0.031 [1825:160]
1 duplicate frame(s)!
Pos: 179.4s   5209f (17%) 1942.93fps Trem:   0min 248mb  A-V:0.033 [1825:160]
demux_mpg: 24000/1001fps progressive NTSC content detected, switching framerate.

1 duplicate frame(s)!
Pos: 179.7s   5217f (17%) 1945.19fps Trem:   0min 248mb  A-V:0.013 [1826:160]
1 duplicate frame(s)!
Pos: 179.9s   5221f (17%) 1943.78fps Trem:   0min 244mb  A-V:0.015 [1825:160]
1 duplicate frame(s)!
Pos: 180.0s   5225f (17%) 1944.55fps Trem:   0min 244mb  A-V:0.017 [1826:160]
1 duplicate frame(s)!
Pos: 180.2s   5229f (17%) 1945.31fps Trem:   0min 245mb  A-V:0.018 [1828:160]
1 duplicate frame(s)!
Pos: 180.4s   5233f (17%) 1931.71fps Trem:   0min 240mb  A-V:0.019 [1829:160]
1 duplicate frame(s)!
Pos: 180.5s   5237f (17%) 1933.19fps Trem:   0min 240mb  A-V:0.021 [1830:160]
1 duplicate frame(s)!
Pos: 180.7s   5241f (17%) 1933.95fps Trem:   0min 240mb  A-V:0.022 [1830:160]
1 duplicate frame(s)!
Pos: 180.9s   5245f (18%) 1934.71fps Trem:   0min 236mb  A-V:0.021 [1830:160]
1 duplicate frame(s)!
Pos: 181.0s   5249f (18%) 1935.47fps Trem:   0min 236mb  A-V:0.021 [1830:160]
1 duplicate frame(s)!
Pos: 181.2s   5253f (18%) 1936.23fps Trem:   0min 236mb  A-V:0.021 [1830:160]
1 duplicate frame(s)!
Pos: 181.4s   5257f (18%) 1787.49fps Trem:   0min 232mb  A-V:0.022 [1831:160]
1 duplicate frame(s)!
Pos: 181.5s   5261f (18%) 1788.85fps Trem:   0min 232mb  A-V:0.022 [1831:160]
1 duplicate frame(s)!
Pos: 181.7s   5265f (18%) 1789.60fps Trem:   0min 232mb  A-V:0.023 [1832:160]
1 duplicate frame(s)!
Pos: 181.9s   5269f (18%) 1788.53fps Trem:   0min 229mb  A-V:0.021 [1832:160]
1 duplicate frame(s)!
Pos: 182.0s   5273f (18%) 1789.28fps Trem:   0min 230mb  A-V:0.022 [1832:160]
1 duplicate frame(s)!
Pos: 182.2s   5277f (18%) 1790.63fps Trem:   0min 230mb  A-V:0.021 [1832:160]
1 duplicate frame(s)!
Pos: 182.4s   5281f (19%) 1788.35fps Trem:   0min 225mb  A-V:0.021 [1831:160]
1 duplicate frame(s)!
Pos: 182.5s   5285f (19%) 1789.10fps Trem:   0min 225mb  A-V:0.021 [1831:160]
1 duplicate frame(s)!
Pos: 182.7s   5289f (19%) 1789.85fps Trem:   0min 225mb  A-V:0.021 [1830:160]
1 duplicate frame(s)!
Pos: 182.9s   5293f (19%) 1784.56fps Trem:   0min 221mb  A-V:0.021 [1830:160]
1 duplicate frame(s)!
Pos: 183.0s   5297f (19%) 1785.30fps Trem:   0min 221mb  A-V:0.021 [1831:160]
1 duplicate frame(s)!
Pos: 183.2s   5301f (19%) 1785.45fps Trem:   0min 221mb  A-V:0.023 [1831:160]
1 duplicate frame(s)!
Pos: 183.4s   5305f (20%) 1783.79fps Trem:   0min 216mb  A-V:0.037 [1832:160]
demux_mpg: 30000/1001fps NTSC content detected, switching framerate.
Warning! FPS changed 23.976 -> 29.970  (-5.994005) [4]   A-V:0.008 [1832:160]
Pos: 233.3s   6802f (56%) 1479.34fps Trem:   0min 101mb  A-V:0.019 [1886:160]
1 duplicate frame(s)!
Pos: 233.5s   6807f (56%) 1480.10fps Trem:   0min 101mb  A-V:0.026 [1887:160]
1 duplicate frame(s)!
Pos: 233.7s   6812f (56%) 1481.19fps Trem:   0min 101mb  A-V:0.029 [1886:160]
1 duplicate frame(s)!
Pos: 233.8s   6813f (56%) 1481.41fps Trem:   0min 101mb  A-V:0.030 [1886:160]
demux_mpg: 24000/1001fps progressive NTSC content detected, switching framerate.
Pos: 233.8s   6814f (56%) 1475.21fps Trem:   0min 100mb  A-V:0.031 [1886:160]
1 duplicate frame(s)!
Pos: 234.1s   6822f (56%) 1476.62fps Trem:   0min 100mb  A-V:0.015 [1885:160]
1 duplicate frame(s)!
Pos: 234.2s   6823f (56%) 1476.52fps Trem:   0min 100mb  A-V:0.019 [1885:160]
demux_mpg: 30000/1001fps NTSC content detected, switching framerate.
Warning! FPS changed 23.976 -> 29.970  (-5.994005) [4]   A-V:0.023 [1885:160]
Pos: 272.4s   7968f (87%) 958.38fps Trem:   0min  78mb  A-V:0.031 [1946:159]]
1 duplicate frame(s)!
Pos: 293.2s   8590f (97%) 998.37fps Trem:   0min  73mb  A-V:-0.004 [1910:159]
1 duplicate frame(s)!
Pos: 295.0s   8644f (99%) 996.43fps Trem:   0min  73mb  A-V:-0.002 [1911:159]]
1 duplicate frame(s)!
TS_PARSE: COULDN'T SYNC%) 998.16fps Trem:   0min  73mb  A-V:-0.000 [1910:159]
Writing index...00f (100%) 1001.04fps Trem:   0min  73mb  A-V:-0.007 [1910:160]
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream: 1910.947 kbit/s  (238868 B/s)  size: 70927192 bytes  296.930 secs  8700 frames

Audio stream:  160.000 kbit/s  (20000 B/s)  size: 5930468 bytes  296.523 secs

```

---

### Post by kmrs75 on 2009-11-14
i have trp files that i wanted to join *.trp and *.001 - the only way that i could get it to work is virtualbox windows and run a program called VIDEOREDO TVSUITE.
from that you can do 2 things. 

one make an iso file and burn it with another program. i use K3b 

or #2 it can join the trp files convert them and then it will burn directly to the dvd.

i cant do the 2nd one having problems with my dvd mounting in virtualbox so i have to go with step #1

---

