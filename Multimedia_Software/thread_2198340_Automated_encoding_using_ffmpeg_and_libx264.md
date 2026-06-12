---
title: "Automated encoding using ffmpeg and libx264"
date: 2014-01-08
forum: Multimedia Software
---

### Post by jokenjp on 2014-01-08
I have a python script that will encode using below command

```
ffmpeg -i a.mkv -tune animation -keyint_min 12 -sc_threshold 45 -bf 8 -b_strategy 2 -refs 10 -qmin 10 -qmax 51 -qcomp 0.6 -direct-pred auto -me_range 24 -me_method umh -subq 9 -trellis 2 -vcodec libx264 -crf 23.0 output.mkv
```

The output.mkv successfully generated but without correct fonts from the original video. How do I output the video the same with original video's font?

---

### Post by mc4man on 2014-01-08
I don't know the answer to your question per se but in such cases concerning the 'ffmpeg' command it's  useful to post - 
What release of Ubuntu do you have
What version of ffmpeg

---

### Post by FakeOutdoorsman on 2014-01-08
Also the complete ffmpeg console output is required information.
I don't quite understand what the issue is.

---

### Post by jokenjp on 2014-01-09
> **mc4man said:**
> I don't know the answer to your question per se but in such cases concerning the 'ffmpeg' command it's  useful to post - 
What release of Ubuntu do you have
What version of ffmpeg

> **FakeOutdoorsman said:**
> Also the complete ffmpeg console output is required information.
I don't quite understand what the issue is.
 
hi i use latest ffmpeg from github and compile it successfully

and encoding does not have problems, the output.mkv plays well it just that the font changes to Arial which the original video uses different font. Any idea why ffmpeg does not use the original video's font?

---

### Post by FakeOutdoorsman on 2014-01-09
Please show your complete ffmpeg console output. Providing a sample input file will also be very useful. We need enough information from you so anyone can attempt to duplicate the issue.

---

### Post by jokenjp on 2014-01-11
below is the ffmpeg output
please have a look, it seems that it can't extract font and uses Arial instead, this changes the output video to have different font from original video
```

[root@ks4003686 Downloads]# ffmpeg -i "[Migoto] Dibetagurashi - 04 (848x480 H264 AAC) [74DB3757].mkv" -tune animation -keyint_min 12 -sc_threshold 45 -bf 8 -b_strategy 2 -refs 10 -qmin 10 -qmax 51 -qcomp 0.6 -direct-pred auto -me_range 24 -me_method umh -subq 9 -trellis 2 -vcodec libx264 -crf 23.0 output.mkv
ffmpeg version 2.0.1 Copyright (c) 2000-2013 the FFmpeg developers
  built on Jan  8 2014 03:23:14 with gcc 4.4.7 (GCC) 20120313 (Red Hat 4.4.7-4)
  configuration: --enable-gpl --enable-version3 --enable-shared --enable-nonfree --enable-postproc --enable-libfaac --enable-libx264
  libavutil      52. 38.100 / 52. 38.100
  libavcodec     55. 18.102 / 55. 18.102
  libavformat    55. 12.100 / 55. 12.100
  libavdevice    55.  3.100 / 55.  3.100
  libavfilter     3. 79.101 /  3. 79.101
  libswscale      2.  3.100 /  2.  3.100
  libswresample   0. 17.102 /  0. 17.102
  libpostproc    52.  3.100 / 52.  3.100
Input #0, matroska,webm, from '[Migoto] Dibetagurashi - 04 (848x480 H264 AAC) [74DB3757].mkv':
  Metadata:
    creation_time   : 2013-09-11 01:08:39
  Duration: 00:03:00.47, start: 0.000000, bitrate: 640 kb/s
    Stream #0:0(jpn): Video: h264 (High), yuv420p, 848x480, SAR 1:1 DAR 53:30, 29.97 fps, 29.97 tbr, 1k tbn, 59.94 tbc (default)
    Metadata:
      title           : Dibetagurashi - 04
    Stream #0:1(jpn): Audio: aac, 48000 Hz, stereo, fltp (default)
    Metadata:
      title           : AAC 2.0
    Stream #0:2(eng): Subtitle: ssa (default)
    Metadata:
      title           : Migoto
Codec 0x18000 is not in the full list.
    Stream #0:3: Attachment: unknown_codec
    Metadata:
      filename        : BRLNSDB.TTF
      mimetype        : application/x-truetype-font
Codec 0x18000 is not in the full list.
    Stream #0:4: Attachment: unknown_codec
    Metadata:
      filename        : Clair.ttf
      mimetype        : application/x-truetype-font
Codec 0x18000 is not in the full list.
    Stream #0:5: Attachment: unknown_codec
    Metadata:
      filename        : KOMTXT.TTF
      mimetype        : application/x-truetype-font
[libx264 @ 0x133b360] using SAR=1/1
[libx264 @ 0x133b360] using cpu capabilities: MMX2 SSE2Fast SSSE3 SSE4.2 AVX
[libx264 @ 0x133b360] profile High, level 3.1
[libx264 @ 0x133b360] 264 - core 138 - H.264/MPEG-4 AVC codec - Copyleft 2003-2013 - http://www.videolan.org/x264.html - options: cabac=1 ref=10 deblock=1:1:1 analyse=0x3:0x113 me=umh subme=9 psy=1 psy_rd=0.40:0.00 mixed_ref=1 me_range=24 chroma_me=1 trellis=2 8x8dct=1 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=-2 threads=6 lookahead_threads=1 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=8 b_pyramid=2 b_adapt=2 b_bias=0 direct=3 weightb=1 open_gop=0 weightp=2 keyint=250 keyint_min=12 scenecut=45 intra_refresh=0 rc_lookahead=40 rc=crf mbtree=1 crf=23.0 qcomp=0.60 qpmin=10 qpmax=51 qpstep=4 ip_ratio=1.40 aq=1:0.60
Output #0, matroska, to 'output.mkv':
  Metadata:
    encoder         : Lavf55.12.100
    Stream #0:0(jpn): Video: h264 (libx264) (H264 / 0x34363248), yuv420p, 848x480 [SAR 1:1 DAR 53:30], q=10-51, 1k tbn, 29.97 tbc (default)
    Metadata:
      title           : Dibetagurashi - 04
    Stream #0:1(jpn): Audio: ac3 ([0] [0][0] / 0x2000), 48000 Hz, stereo, fltp, 192 kb/s (default)
    Metadata:
      title           : AAC 2.0
    Stream #0:2(eng): Subtitle: ssa (default)
    Metadata:
      title           : Migoto
Stream mapping:
  Stream #0:0 -> #0:0 (h264 -> libx264)
  Stream #0:1 -> #0:1 (aac -> ac3)
  Stream #0:2 -> #0:2 (ssa -> ssa)
Press [q] to stop, [?] for help
frame=   51 fps=0.0 q=0.0 size=       2kB time=00:00:01.88 bitrate=   7.9kbits/sframe=   78 fps= 77 q=29.0 size=       2kB time=00:00:02.84 bitrate=   5.2kbits/frame=  101 fps= 66 q=29.0 size=       2kB time=00:00:03.51 bitrate=   4.2kbits/frame=  129 fps= 63 q=29.0 size=       2kB time=00:00:04.53 bitrate=   3.3kbits/frame=  153 fps= 59 q=29.0 size=       2kB time=00:00:05.37 bitrate=   2.8kbits/frame=  168 fps= 54 q=29.0 size=     235kB time=00:00:05.88 bitrate= 327.2kbits/frame=  181 fps= 50 q=29.0 size=     300kB time=00:00:06.33 bitrate= 388.0kbits/frame=  194 fps= 47 q=29.0 size=     361kB time=00:00:06.71 bitrate= 440.8kbits/frame=  208 fps= 45 q=29.0 size=     408kB time=00:00:07.19 bitrate= 464.2kbits/frame=  223 fps= 43 q=29.0 size=     456kB time=00:00:07.70 bitrate= 484.9kbits/frame=  237 fps= 42 q=29.0 size=     470kB time=00:00:08.18 bitrate= 470.1kbits/frame=  252 fps= 41 q=29.0 size=     470kB time=00:00:08.69 bitrate= 442.4kbits/frame=  265 fps= 39 q=29.0 size=     470kB time=00:00:09.01 bitrate= 426.7kbits/frame=  280 fps= 38 q=29.0 size=     470kB time=00:00:09.53 bitrate= 403.8kbits/frame=  293 fps= 37 q=29.0 size=     470kB time=00:00:10.04 bitrate= 383.2kbits/frame=  308 fps= 37 q=29.0 size=     470kB time=00:00:10.52 bitrate= 365.7kbits/frame=  317 fps= 36 q=29.0 size=     470kB time=00:00:10.87 bitrate= 353.9kbits/frame=  333 fps= 35 q=29.0 size=     470kB time=00:00:11.38 bitrate= 338.0kbits/frame=  344 fps= 35 q=29.0 size=     470kB time=00:00:11.70 bitrate= 328.7kbits/frame=  355 fps= 34 q=29.0 size=     470kB time=00:00:12.02 bitrate= 320.0kbits/frame=  371 fps= 34 q=29.0 size=     470kB time=00:00:12.69 bitrate= 303.1kbits/frame=  385 fps= 34 q=29.0 size=     470kB time=00:00:13.05 bitrate= 294.9kbits/frame=  403 fps= 33 q=29.0 size=     470kB time=00:00:13.72 bitrate= 280.4kbits/frame=  419 fps= 33 q=29.0 size=     470kB time=00:00:14.20 bitrate= 271.0kbits/frame=  426 fps= 32 q=29.0 size=     470kB time=00:00:14.52 bitrate= 265.0kbits/frame=  439 fps= 32 q=29.0 size=     470kB time=00:00:14.87 bitrate= 258.7kbits/frame=  457 fps= 32 q=29.0 size=     470kB time=00:00:15.54 bitrate= 247.5kbits/frame=  475 fps= 32 q=29.0 size=     470kB time=00:00:16.02 bitrate= 240.1kbits/frame=  494 fps= 32 q=29.0 size=     470kB time=00:00:16.69 bitrate= 230.4kbits/frame=  506 fps= 32 q=29.0 size=     470kB time=00:00:17.05 bitrate= 225.7kbits/frame=  533 fps= 33 q=29.0 size=     470kB time=00:00:18.04 bitrate= 213.3kbits/frame=  552 fps= 33 q=29.0 size=    1669kB time=00:00:18.71 bitrate= 730.4kbits/frame=  561 fps= 32 q=29.0 size=    1719kB time=00:00:19.06 bitrate= 738.4kbits/frame=  576 fps= 32 q=29.0 size=    1777kB time=00:00:19.57 bitrate= 743.6kbits/frame=  595 fps= 32 q=29.0 size=    1835kB time=00:00:20.05 bitrate= 749.6kbits/frame=  630 fps= 33 q=29.0 size=    1881kB time=00:00:21.30 bitrate= 723.2kbits/frame=  688 fps= 35 q=29.0 size=    1881kB time=00:00:23.22 bitrate= 663.4kbits/frame=  747 fps= 37 q=29.0 size=    2034kB time=00:00:25.24 bitrate= 660.0kbits/frame=  802 fps= 39 q=29.0 size=    2079kB time=00:00:27.06 bitrate= 629.2kbits/frame=  843 fps= 40 q=29.0 size=    2079kB time=00:00:28.41 bitrate= 599.5kbits/frame=  867 fps= 40 q=29.0 size=    2079kB time=00:00:29.11 bitrate= 585.0kbits/frame=  886 fps= 40 q=29.0 size=    2079kB time=00:00:29.94 bitrate= 568.7kbits/frame=  903 fps= 40 q=29.0 size=    2079kB time=00:00:30.39 bitrate= 560.3kbits/frame=  915 fps= 40 q=29.0 size=    2309kB time=00:00:30.74 bitrate= 615.1kbits/frame=  924 fps= 39 q=29.0 size=    2372kB time=00:00:31.09 bitrate= 624.9kbits/frame=  941 fps= 39 q=29.0 size=    2409kB time=00:00:31.77 bitrate= 621.2kbits/frame=  970 fps= 39 q=29.0 size=    2445kB time=00:00:32.57 bitrate= 614.9kbits/frame=  996 fps= 39 q=29.0 size=    2473kB time=00:00:33.46 bitrate= 605.3kbits/frame= 1025 fps= 40 q=29.0 size=    2503kB time=00:00:34.42 bitrate= 595.6kbits/frame= 1032 fps= 39 q=29.0 size=    2526kB time=00:00:34.61 bitrate= 597.7kbits/frame= 1042 fps= 39 q=29.0 size=    2577kB time=00:00:35.09 bitrate= 601.5kbits/frame= 1057 fps= 38 q=29.0 size=    2590kB time=00:00:35.45 bitrate= 598.5kbits/frame= 1071 fps= 38 q=29.0 size=    2590kB time=00:00:35.96 bitrate= 590.0kbits/frame= 1081 fps= 38 q=29.0 size=    2590kB time=00:00:36.41 bitrate= 582.7kbits/frame= 1099 fps= 38 q=29.0 size=    2590kB time=00:00:36.92 bitrate= 574.6kbits/frame= 1120 fps= 38 q=29.0 size=    2590kB time=00:00:37.62 bitrate= 563.9kbits/frame= 1140 fps= 38 q=29.0 size=    2590kB time=00:00:38.26 bitrate= 554.5kbits/frame= 1183 fps= 38 q=29.0 size=    2590kB time=00:00:39.80 bitrate= 533.1kbits/frame= 1216 fps= 39 q=29.0 size=    2590kB time=00:00:40.76 bitrate= 520.5kbits/frame= 1247 fps= 39 q=29.0 size=    2954kB time=00:00:41.78 bitrate= 579.2kbits/frame= 1275 fps= 39 q=29.0 size=    2998kB time=00:00:42.77 bitrate= 574.1kbits/frame= 1296 fps= 39 q=29.0 size=    3035kB time=00:00:43.45 bitrate= 572.2kbits/frame= 1320 fps= 39 q=29.0 size=    3035kB time=00:00:44.28 bitrate= 561.4kbits/frame= 1328 fps= 39 q=29.0 size=    3035kB time=00:00:44.60 bitrate= 557.4kbits/frame= 1347 fps= 39 q=29.0 size=    3035kB time=00:00:45.30 bitrate= 548.8kbits/frame= 1372 fps= 39 q=29.0 size=    3035kB time=00:00:45.97 bitrate= 540.7kbits/frame= 1397 fps= 39 q=29.0 size=    3319kB time=00:00:46.77 bitrate= 581.2kbits/frame= 1426 fps= 40 q=29.0 size=    3362kB time=00:00:47.80 bitrate= 576.1kbits/frame= 1467 fps= 40 q=29.0 size=    3404kB time=00:00:49.14 bitrate= 567.4kbits/frame= 1511 fps= 41 q=29.0 size=    3474kB time=00:00:50.65 bitrate= 561.8kbits/frame= 1557 fps= 41 q=29.0 size=    3497kB time=00:00:52.12 bitrate= 549.7kbits/frame= 1601 fps= 42 q=29.0 size=    3564kB time=00:00:53.65 bitrate= 544.1kbits/frame= 1618 fps= 42 q=29.0 size=    3601kB time=00:00:54.29 bitrate= 543.2kbits/frame= 1645 fps= 42 q=29.0 size=    3640kB time=00:00:55.16 bitrate= 540.5kbits/frame= 1673 fps= 42 q=29.0 size=    3680kB time=00:00:55.99 bitrate= 538.3kbits/frame= 1683 fps= 42 q=29.0 size=    3728kB time=00:00:56.47 bitrate= 540.7kbits/frame= 1709 fps= 42 q=29.0 size=    3740kB time=00:00:57.33 bitrate= 534.3kbits/frame= 1734 fps= 42 q=29.0 size=    3806kB time=00:00:58.04 bitrate= 537.2kbits/frame= 1765 fps= 42 q=29.0 size=    3866kB time=00:00:59.16 bitrate= 535.3kbits/frame= 1793 fps= 42 q=29.0 size=    3899kB time=00:01:00.02 bitrate= 532.1kbits/frame= 1819 fps= 43 q=29.0 size=    3951kB time=00:01:00.98 bitrate= 530.7kbits/frame= 1842 fps= 43 q=29.0 size=    3986kB time=00:01:01.69 bitrate= 529.3kbits/frame= 1868 fps= 43 q=29.0 size=    4033kB time=00:01:02.65 bitrate= 527.3kbits/frame= 1895 fps= 43 q=29.0 size=    4049kB time=00:01:03.51 bitrate= 522.3kbits/frame= 1920 fps= 43 q=29.0 size=    4049kB time=00:01:04.31 bitrate= 515.8kbits/frame= 1945 fps= 43 q=29.0 size=    4049kB time=00:01:05.17 bitrate= 508.9kbits/frame= 1968 fps= 43 q=29.0 size=    4049kB time=00:01:05.85 bitrate= 503.7kbits/frame= 1991 fps= 43 q=29.0 size=    4049kB time=00:01:06.68 bitrate= 497.5kbits/frame= 2017 fps= 43 q=29.0 size=    4297kB time=00:01:07.54 bitrate= 521.2kbits/frame= 2040 fps= 43 q=29.0 size=    4341kB time=00:01:08.34 bitrate= 520.3kbits/frame= 2062 fps= 43 q=29.0 size=    4380kB time=00:01:09.17 bitrate= 518.7kbits/frame= 2081 fps= 43 q=29.0 size=    4421kB time=00:01:09.69 bitrate= 519.7kbits/frame= 2103 fps= 43 q=29.0 size=    4458kB time=00:01:10.52 bitrate= 517.9kbits/frame= 2124 fps= 43 q=29.0 size=    4493kB time=00:01:11.19 bitrate= 517.0kbits/frame= 2144 fps= 43 q=29.0 size=    4533kB time=00:01:11.86 bitrate= 516.8kbits/frame= 2163 fps= 43 q=29.0 size=    4569kB time=00:01:12.50 bitrate= 516.2kbits/frame= 2184 fps= 43 q=29.0 size=    4577kB time=00:01:13.05 bitrate= 513.3kbits/frame= 2205 fps= 43 q=29.0 size=    4639kB time=00:01:13.88 bitrate= 514.4kbits/frame= 2227 fps= 43 q=29.0 size=    4676kB time=00:01:14.52 bitrate= 514.0kbits/frame= 2247 fps= 43 q=29.0 size=    4754kB time=00:01:15.19 bitrate= 518.0kbits/frame= 2273 fps= 43 q=29.0 size=    4796kB time=00:01:16.05 bitrate= 516.5kbits/frame= 2294 fps= 43 q=29.0 size=    4831kB time=00:01:16.85 bitrate= 514.9kbits/frame= 2317 fps= 43 q=29.0 size=    4875kB time=00:01:17.56 bitrate= 514.8kbits/frame= 2334 fps= 43 q=29.0 size=    4912kB time=00:01:18.07 bitrate= 515.4kbits/frame= 2361 fps= 43 q=29.0 size=    4913kB time=00:01:19.06 bitrate= 509.0kbits/frame= 2395 fps= 43 q=29.0 size=    4977kB time=00:01:20.05 bitrate= 509.3kbits/frame= 2431 fps= 43 q=29.0 size=    5016kB time=00:01:21.40 bitrate= 504.8kbits/frame= 2465 fps= 43 q=29.0 size=    5022kB time=00:01:22.55 bitrate= 498.3kbits/frame= 2494 fps= 44 q=29.0 size=    5022kB time=00:01:23.57 bitrate= 492.2kbits/frame= 2516 fps= 44 q=29.0 size=    5022kB time=00:01:24.21 bitrate= 488.5kbits/frame= 2541 fps= 44 q=29.0 size=    5193kB time=00:01:25.05 bitrate= 500.2kbits/frame= 2559 fps= 44 q=29.0 size=    5218kB time=00:01:25.59 bitrate= 499.4kbits/frame= 2594 fps= 44 q=29.0 size=    5270kB time=00:01:26.71 bitrate= 497.9kbits/frame= 2627 fps= 44 q=29.0 size=    5274kB time=00:01:27.93 bitrate= 491.3kbits/frame= 2656 fps= 44 q=29.0 size=    5344kB time=00:01:28.89 bitrate= 492.5kbits/frame= 2684 fps= 44 q=29.0 size=    5376kB time=00:01:29.78 bitrate= 490.5kbits/frame= 2716 fps= 44 q=29.0 size=    5411kB time=00:01:30.90 bitrate= 487.7kbits/frame= 2750 fps= 44 q=29.0 size=    5451kB time=00:01:31.93 bitrate= 485.8kbits/frame= 2782 fps= 45 q=29.0 size=    5458kB time=00:01:33.08 bitrate= 480.3kbits/frame= 2814 fps= 45 q=29.0 size=    5458kB time=00:01:34.23 bitrate= 474.5kbits/frame= 2864 fps= 45 q=29.0 size=    5458kB time=00:01:35.77 bitrate= 466.8kbits/frame= 2896 fps= 45 q=29.0 size=    5458kB time=00:01:36.92 bitrate= 461.3kbits/frame= 2918 fps= 45 q=29.0 size=    5458kB time=00:01:37.62 bitrate= 458.0kbits/frame= 2938 fps= 45 q=29.0 size=    5458kB time=00:01:38.42 bitrate= 454.2kbits/frame= 2955 fps= 45 q=29.0 size=    5458kB time=00:01:38.93 bitrate= 451.9kbits/frame= 2972 fps= 45 q=29.0 size=    5458kB time=00:01:39.45 bitrate= 449.6kbits/frame= 2990 fps= 45 q=29.0 size=    5800kB time=00:01:39.96 bitrate= 475.3kbits/frame= 3018 fps= 45 q=29.0 size=    5847kB time=00:01:40.92 bitrate= 474.6kbits/frame= 3043 fps= 45 q=29.0 size=    5892kB time=00:01:41.78 bitrate= 474.2kbits/frame= 3056 fps= 45 q=29.0 size=    5892kB time=00:01:42.20 bitrate= 472.3kbits/frame= 3076 fps= 45 q=29.0 size=    5892kB time=00:01:42.93 bitrate= 468.9kbits/frame= 3092 fps= 45 q=29.0 size=    5892kB time=00:01:43.45 bitrate= 466.6kbits/frame= 3127 fps= 45 q=29.0 size=    6085kB time=00:01:44.76 bitrate= 475.8kbits/frame= 3168 fps= 45 q=29.0 size=    6154kB time=00:01:45.97 bitrate= 475.7kbits/frame= 3204 fps= 45 q=29.0 size=    6154kB time=00:01:47.13 bitrate= 470.6kbits/frame= 3233 fps= 45 q=29.0 size=    6154kB time=00:01:48.15 bitrate= 466.2kbits/frame= 3261 fps= 45 q=29.0 size=    6154kB time=00:01:49.11 bitrate= 462.1kbits/frame= 3284 fps= 45 q=29.0 size=    6154kB time=00:01:49.81 bitrate= 459.1kbits/frame= 3306 fps= 45 q=29.0 size=    6358kB time=00:01:50.61 bitrate= 470.8kbits/frame= 3336 fps= 46 q=29.0 size=    6393kB time=00:01:51.64 bitrate= 469.1kbits/frame= 3362 fps= 46 q=29.0 size=    6444kB time=00:01:52.44 bitrate= 469.5kbits/frame= 3376 fps= 45 q=29.0 size=    6444kB time=00:01:52.95 bitrate= 467.4kbits/frame= 3393 fps= 45 q=29.0 size=    6444kB time=00:01:53.46 bitrate= 465.2kbits/frame= 3408 fps= 45 q=29.0 size=    6444kB time=00:01:53.97 bitrate= 463.2kbits/frame= 3426 fps= 45 q=29.0 size=    6444kB time=00:01:54.61 bitrate= 460.6kbits/frame= 3445 fps= 45 q=29.0 size=    6444kB time=00:01:55.16 bitrate= 458.4kbits/frame= 3470 fps= 45 q=29.0 size=    6444kB time=00:01:55.99 bitrate= 455.1kbits/frame= 3503 fps= 45 q=29.0 size=    6739kB time=00:01:57.14 bitrate= 471.3kbits/frame= 3533 fps= 45 q=29.0 size=    6785kB time=00:01:58.17 bitrate= 470.4kbits/frame= 3556 fps= 45 q=29.0 size=    6785kB time=00:01:58.97 bitrate= 467.2kbits/frame= 3574 fps= 45 q=29.0 size=    6862kB time=00:01:59.48 bitrate= 470.4kbits/frame= 3604 fps= 45 q=29.0 size=    6926kB time=00:02:00.47 bitrate= 470.9kbits/frame= 3632 fps= 45 q=29.0 size=    6956kB time=00:02:01.49 bitrate= 469.0kbits/frame= 3657 fps= 45 q=29.0 size=    7003kB time=00:02:02.29 bitrate= 469.1kbits/frame= 3684 fps= 45 q=29.0 size=    7043kB time=00:02:03.16 bitrate= 468.5kbits/frame= 3711 fps= 45 q=29.0 size=    7082kB time=00:02:04.02 bitrate= 467.8kbits/frame= 3737 fps= 45 q=29.0 size=    7117kB time=00:02:04.98 bitrate= 466.5kbits/frame= 3766 fps= 45 q=29.0 size=    7169kB time=00:02:06.01 bitrate= 466.1kbits/frame= 3795 fps= 46 q=29.0 size=    7177kB time=00:02:06.84 bitrate= 463.5kbits/frame= 3821 fps= 46 q=29.0 size=    7177kB time=00:02:07.67 bitrate= 460.5kbits/frame= 3846 fps= 46 q=29.0 size=    7177kB time=00:02:08.66 bitrate= 457.0kbits/frame= 3871 fps= 46 q=29.0 size=    7177kB time=00:02:09.37 bitrate= 454.5kbits/frame= 3903 fps= 46 q=29.0 size=    7177kB time=00:02:10.49 bitrate= 450.6kbits/frame= 3929 fps= 46 q=29.0 size=    7385kB time=00:02:11.38 bitrate= 460.5kbits/frame= 3957 fps= 46 q=29.0 size=    7416kB time=00:02:12.34 bitrate= 459.0kbits/frame= 3981 fps= 46 q=29.0 size=    7471kB time=00:02:13.01 bitrate= 460.1kbits/frame= 4006 fps= 46 q=29.0 size=    7471kB time=00:02:13.88 bitrate= 457.1kbits/frame= 4034 fps= 46 q=29.0 size=    7540kB time=00:02:14.84 bitrate= 458.1kbits/frame= 4044 fps= 46 q=29.0 size=    7579kB time=00:02:15.19 bitrate= 459.2kbits/frame= 4072 fps= 46 q=29.0 size=    7609kB time=00:02:16.05 bitrate= 458.2kbits/frame= 4104 fps= 46 q=29.0 size=    7644kB time=00:02:17.21 bitrate= 456.4kbits/frame= 4136 fps= 46 q=29.0 size=    7644kB time=00:02:18.23 bitrate= 453.0kbits/frame= 4169 fps= 46 q=29.0 size=    7734kB time=00:02:19.38 bitrate= 454.5kbits/frame= 4199 fps= 46 q=29.0 size=    7794kB time=00:02:20.34 bitrate= 454.9kbits/frame= 4219 fps= 46 q=29.0 size=    7813kB time=00:02:21.05 bitrate= 453.8kbits/frame= 4241 fps= 46 q=29.0 size=    7813kB time=00:02:21.75 bitrate= 451.5kbits/frame= 4256 fps= 46 q=29.0 size=    7813kB time=00:02:22.23 bitrate= 450.0kbits/frame= 4270 fps= 46 q=29.0 size=    7813kB time=00:02:22.71 bitrate= 448.5kbits/frame= 4287 fps= 46 q=29.0 size=    7813kB time=00:02:23.38 bitrate= 446.4kbits/frame= 4304 fps= 46 q=29.0 size=    7992kB time=00:02:23.89 bitrate= 455.0kbits/frame= 4324 fps= 46 q=29.0 size=    8045kB time=00:02:24.53 bitrate= 456.0kbits/frame= 4347 fps= 46 q=29.0 size=    8088kB time=00:02:25.21 bitrate= 456.3kbits/frame= 4372 fps= 46 q=29.0 size=    8111kB time=00:02:26.07 bitrate= 454.9kbits/frame= 4397 fps= 46 q=29.0 size=    8111kB time=00:02:26.90 bitrate= 452.3kbits/frame= 4427 fps= 46 q=29.0 size=    8111kB time=00:02:28.09 bitrate= 448.7kbits/frame= 4454 fps= 46 q=29.0 size=    8111kB time=00:02:28.89 bitrate= 446.3kbits/frame= 4470 fps= 46 q=29.0 size=    8111kB time=00:02:29.40 bitrate= 444.8kbits/frame= 4481 fps= 45 q=29.0 size=    8111kB time=00:02:29.75 bitrate= 443.7kbits/frame= 4520 fps= 46 q=29.0 size=    8321kB time=00:02:31.06 bitrate= 451.2kbits/frame= 4577 fps= 46 q=29.0 size=    8408kB time=00:02:32.92 bitrate= 450.4kbits/frame= 4631 fps= 46 q=29.0 size=    8408kB time=00:02:34.74 bitrate= 445.1kbits/frame= 4672 fps= 46 q=29.0 size=    8503kB time=00:02:36.12 bitrate= 446.1kbits/frame= 4709 fps= 47 q=29.0 size=    8536kB time=00:02:37.43 bitrate= 444.1kbits/frame= 4741 fps= 47 q=29.0 size=    8536kB time=00:02:38.39 bitrate= 441.5kbits/frame= 4776 fps= 47 q=29.0 size=    8628kB time=00:02:39.61 bitrate= 442.8kbits/frame= 4822 fps= 47 q=29.0 size=    8685kB time=00:02:41.08 bitrate= 441.7kbits/frame= 4874 fps= 47 q=29.0 size=    8685kB time=00:02:42.93 bitrate= 436.7kbits/frame= 4929 fps= 47 q=29.0 size=    8818kB time=00:02:44.76 bitrate= 438.4kbits/frame= 4981 fps= 48 q=29.0 size=    8865kB time=00:02:46.42 bitrate= 436.3kbits/frame= 5018 fps= 48 q=29.0 size=    8911kB time=00:02:47.61 bitrate= 435.5kbits/frame= 5045 fps= 48 q=29.0 size=    8911kB time=00:02:48.63 bitrate= 432.9kbits/frame= 5077 fps= 48 q=29.0 size=    8911kB time=00:02:49.65 bitrate= 430.3kbits/frame= 5108 fps= 48 q=29.0 size=    9061kB time=00:02:50.61 bitrate= 435.1kbits/frame= 5140 fps= 48 q=29.0 size=    9110kB time=00:02:51.80 bitrate= 434.4kbits/frame= 5170 fps= 48 q=29.0 size=    9150kB time=00:02:52.79 bitrate= 433.8kbits/frame= 5197 fps= 48 q=29.0 size=    9150kB time=00:02:53.62 bitrate= 431.7kbits/frame= 5227 fps= 48 q=29.0 size=    9232kB time=00:02:54.77 bitrate= 432.7kbits/frame= 5265 fps= 48 q=29.0 size=    9309kB time=00:02:55.99 bitrate= 433.3kbits/frame= 5306 fps= 48 q=29.0 size=    9372kB time=00:02:57.30 bitrate= 433.0kbits/frame= 5338 fps= 48 q=29.0 size=    9423kB time=00:02:58.36 bitrate= 432.8kbits/frame= 5383 fps= 49 q=29.0 size=    9467kB time=00:02:59.83 bitrate= 431.3kbits/frame= 5395 fps= 49 q=-1.0 Lsize=    9593kB time=00:03:00.09 bitrate= 436.3kbits/s
video:5291kB audio:4221kB subtitle:4 global headers:1kB muxing overhead 0.791442%
[libx264 @ 0x133b360] frame I:44    Avg QP:17.88  size: 16959
[libx264 @ 0x133b360] frame P:1334  Avg QP:21.72  size:  2503
[libx264 @ 0x133b360] frame B:4017  Avg QP:26.08  size:   332
[libx264 @ 0x133b360] consecutive B-frames:  3.4%  5.3%  4.6% 47.6%  7.2% 14.1%  5.1%  9.0%  3.7%
[libx264 @ 0x133b360] mb I  I16..4: 30.4% 44.8% 24.8%
[libx264 @ 0x133b360] mb P  I16..4:  1.7%  2.8%  0.8%  P16..4: 20.1%  4.8%  2.0%  0.0%  0.0%    skip:67.9%
[libx264 @ 0x133b360] mb B  I16..4:  0.1%  0.1%  0.0%  B16..8:  9.9%  0.7%  0.1%  direct: 0.1%  skip:88.9%  L0:44.1% L1:52.6% BI: 3.3%
[libx264 @ 0x133b360] 8x8 transform intra:49.6% inter:44.3%
[libx264 @ 0x133b360] direct mvs  spatial:99.5% temporal:0.5%
[libx264 @ 0x133b360] coded y,uvDC,uvAC intra: 17.7% 30.3% 13.5% inter: 1.3% 2.2% 0.4%
[libx264 @ 0x133b360] i16 v,h,dc,p: 39% 38%  7% 16%
[libx264 @ 0x133b360] i8 v,h,dc,ddl,ddr,vr,hd,vl,hu: 28% 14% 49%  2%  1%  1%  1%  1%  3%
[libx264 @ 0x133b360] i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 24% 19% 22%  7%  6%  5%  5%  5%  7%
[libx264 @ 0x133b360] i8c dc,h,v,p: 65% 20% 11%  3%
[libx264 @ 0x133b360] Weighted P-Frames: Y:1.8% UV:1.5%
[libx264 @ 0x133b360] ref P L0: 55.9%  5.6% 14.1%  7.3%  5.2%  4.3%  3.1%  1.5%  1.3%  1.7%  0.2%  0.0%
[libx264 @ 0x133b360] ref B L0: 74.0% 10.1%  5.8%  4.2%  2.1%  1.9%  0.9%  0.6%  0.4%
[libx264 @ 0x133b360] ref B L1: 95.6%  4.4%
[libx264 @ 0x133b360] kb/s:240.75

```

---

### Post by FakeOutdoorsman on 2014-01-11
Why are you re-encoding in the first place? It's not like you're changing formats.

I'm not sure why none of the attachments appear to be included. Default stream selection should include one stream per stream type. You can try adding "-map 0:t -codec:t copy", but I'm unsure if it will work as expected since I do not have a sample file.

Why are you not using an encoding preset? The preset will include most of your options you manually added. The "slower" or "veryslow" presets will be most like your options:
```
ffmpeg -i input -codec:v libx264 -crf 23 -preset slower -tune animation -codec:a copy -map 0:t -codec:t copy output.mkv
```

---

### Post by jokenjp on 2014-01-12
hi

I have included preset to veryslow but still it is not copying the font files, and when I use your syntax, it does not able to generate output and show below
I am encoding it to make it smaller size
```
[root@ks4003686 Downloads]# ffmpeg -i "[Migoto] Dibetagurashi - 04 (848x480 H264
 AAC) [74DB3757].mkv" -codec:v libx264 -crf 23 -preset slower -tune animation -c
odec:a copy -map 0:t -codec:t copy output.mkv
ffmpeg version N-59766-ge11983b Copyright (c) 2000-2014 the FFmpeg developers
  built on Jan 11 2014 10:17:05 with gcc 4.4.7 (GCC) 20120313 (Red Hat 4.4.7-4)
  configuration: --prefix=/root/ffmpeg_build --extra-cflags=-I/root/ffmpeg_build
/include --extra-ldflags=-L/root/ffmpeg_build/lib --bindir=/root/bin --extra-lib
s=-ldl --enable-gpl --enable-libass --enable-libfdk-aac --enable-libmp3lame --en
able-libopus --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx
264 --enable-nonfree
  libavutil      52. 62.100 / 52. 62.100
  libavcodec     55. 47.101 / 55. 47.101
  libavformat    55. 22.103 / 55. 22.103
  libavdevice    55.  5.102 / 55.  5.102
  libavfilter     4.  1.100 /  4.  1.100
  libswscale      2.  5.101 /  2.  5.101
  libswresample   0. 17.104 /  0. 17.104
  libpostproc    52.  3.100 / 52.  3.100
Input #0, matroska,webm, from '[Migoto] Dibetagurashi - 04 (848x480 H264 AAC) [7
4DB3757].mkv':
  Metadata:
    encoder         : libebml v1.0.0 + libmatroska v1.0.0
    creation_time   : 2013-09-11 01:08:39
  Duration: 00:03:00.47, start: 0.000000, bitrate: 640 kb/s
    Stream #0:0(jpn): Video: h264 (High), yuv420p, 848x480, SAR 1:1 DAR 53:30, 2
9.97 fps, 29.97 tbr, 1k tbn, 59.94 tbc (default)
    Metadata:
      title           : Dibetagurashi - 04
    Stream #0:1(jpn): Audio: aac, 48000 Hz, stereo, fltp (default)
    Metadata:
      title           : AAC 2.0
    Stream #0:2(eng): Subtitle: ssa (default)
    Metadata:
      title           : Migoto
Codec 0x18000 is not in the full list.
    Stream #0:3: Attachment: unknown_codec
    Metadata:
      filename        : BRLNSDB.TTF
      mimetype        : application/x-truetype-font
Codec 0x18000 is not in the full list.
    Stream #0:4: Attachment: unknown_codec
    Metadata:
      filename        : Clair.ttf
      mimetype        : application/x-truetype-font
Codec 0x18000 is not in the full list.
    Stream #0:5: Attachment: unknown_codec
    Metadata:
      filename        : KOMTXT.TTF
      mimetype        : application/x-truetype-font
Codec AVOption crf (Select the quality for constant quality mode) specified for
output file #0 (output.mkv) has not been used for any stream. The most likely re
ason is either wrong type (e.g. a video option with no video streams) or that it
 is a private option of some encoder which was not actually used for any stream.
Codec AVOption preset (Set the encoding preset (cf. x264 --fullhelp)) specified
for output file #0 (output.mkv) has not been used for any stream. The most likel
y reason is either wrong type (e.g. a video option with no video streams) or tha
t it is a private option of some encoder which was not actually used for any str
eam.
Codec AVOption tune (Tune the encoding params (cf. x264 --fullhelp)) specified f
or output file #0 (output.mkv) has not been used for any stream. The most likely
 reason is either wrong type (e.g. a video option with no video streams) or that
 it is a private option of some encoder which was not actually used for any stre
am.
Output #0, matroska, to 'output.mkv':
  Metadata:
    encoder         : Lavf55.22.103
Codec 0x18000 is not in the full list.
    Stream #0:0: Attachment: unknown_codec
    Metadata:
      filename        : BRLNSDB.TTF
      mimetype        : application/x-truetype-font
Codec 0x18000 is not in the full list.
    Stream #0:1: Attachment: unknown_codec
    Metadata:
      filename        : Clair.ttf
      mimetype        : application/x-truetype-font
Codec 0x18000 is not in the full list.
    Stream #0:2: Attachment: unknown_codec
    Metadata:
      filename        : KOMTXT.TTF
      mimetype        : application/x-truetype-font
Stream mapping:
  Stream #0:3 -> #0:0 (copy)
  Stream #0:4 -> #0:1 (copy)
  Stream #0:5 -> #0:2 (copy)
Press [q] to stop, [?] for help
size=     149kB time=00:00:00.00 bitrate=N/A
video:0kB audio:0kB subtitle:0 global headers:0kB muxing overhead inf%
Output file is empty, nothing was encoded (check -ss / -t / -frames parameters i
f used)

```

---

### Post by FakeOutdoorsman on 2014-01-12
Can you provide the input file?

---

### Post by jokenjp on 2014-01-12
download it from [http://www.sorainnosia.com/Content/a.png](http://www.sorainnosia.com/Content/a.png) then rename to a.mkv

---

