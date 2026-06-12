---
title: "Mencoder : Forcing non-interleaved mode with the -ni option"
date: 2013-03-09
forum: Multimedia Software
---

### Post by Jacques Duflos on 2013-03-09
Hello there,
I have been trying to encode my .ogv videos (made by RecordMyDesktop) to a .avi video to be able to compile it with KDEnlive or other programs.
Besides many forum threads, I have not been able to do so.

First try : Mencoder.
 ```
$mencoder -idx test.ogv -ni -ovc lavc -lavcopts vcodec=mpeg4 -oac mp3lame -o test.avi
MEncoder svn r34540 (Ubuntu), built with gcc-4.7 (C) 2000-2012 MPlayer Team
success: format: 0  data: 0x0 - 0xc613c7d
libavformat version 53.21.1 (external)
Mismatching header version 53.19.0
libavformat file format detected.
[ogg @ 0xb6b445e0]max_analyze_duration reached
[lavf] stream 1: video (theora), -vid 0
[lavf] stream 2: audio (vorbis), -aid 0
VIDEO:  [theo]  1280x800  0bpp  15.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:44  fourcc:0x6F656874  size:1280x800  fps:15.000  ftime:=0.0667
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
libavcodec version 53.35.0 (external)
Mismatching header version 53.32.2
AUDIO: 22050 Hz, 1 ch, s16le, 90.0 kbit/25.51% (ratio: 11248->44100)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis)
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [fftheora] vfm: ffmpeg (FFmpeg Theora)
==========================================================================
MP3 audio selected.
Movie-Aspect is 1.60:1 - prescaling to correct movie aspect.
videocodec: libavcodec (1280x800 fourcc=34504d46 [FMP4])
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Pos:   0.1s      2f ( 0%)  0.00fps Trem:   0min  25mb  A-V:0.007 [0:0]
[VD_FFMPEG] DRI failure.
Pos:   3.0s     45f ( 0%)  0.00fps Trem:   2min  46mb  A-V:-0.133 [563:76]

1 duplicate frame(s)!
Pos:   3.7s     55f ( 0%)  0.00fps Trem:   2min  49mb  A-V:-0.133 [468:80]

1 duplicate frame(s)!
Pos:   4.5s     65f ( 0%)  0.00fps Trem:   3min  52mb  A-V:-0.133 [408:83]

1 duplicate frame(s)!
Pos:   5.2s     75f ( 0%) 67.26fps Trem:   3min  56mb  A-V:-0.133 [366:83]


...........................


1 duplicate frame(s)!
Pos: 112.3s   1535f ( 7%) 76.69fps Trem:   4min 114mb  A-V:-0.133 [542:84]

1 duplicate frame(s)!
Pos: 113.0s   1545f ( 7%) 76.72fps Trem:   4min 114mb  A-V:-0.133 [539:84]

1 duplicate frame(s)!
Pos: 113.5s   1551f ( 7%) 76.74fps Trem:   4min 114mb  A-V:-0.107 [537:84]

Too many audio packets in the buffer: (4096 in 819846 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Flushing video frames.
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream:  537.671 kbit/s  (67208 B/s)  size: 7625968 bytes  113.467 secs  1551 frames

Audio stream:   84.661 kbit/s  (10582 B/s)  size: 1206129 bytes  113.972 secs

```
As you can see, every duplicated frames are deleted. I guess a solution would be to use the -ni option as recommended but when I use this option in the line, it is just ignored.

Second try : ffmpeg
```
$ ffmpeg -i test.ogv -y test.avi
ffmpeg version git-2013-03-06-c257fe1 Copyright (c) 2000-2013 the FFmpeg developers
  built on Mar  6 2013 23:06:39 with gcc 4.7 (Ubuntu/Linaro 4.7.2-2ubuntu1)
  configuration: --enable-gpl --enable-libass --enable-libfaac --enable-libfdk-aac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libspeex --enable-librtmp --enable-libtheora --enable-libvorbis --enable-libvpx --enable-x11grab --enable-libx264 --enable-nonfree --enable-version3
  libavutil      52. 17.103 / 52. 17.103
  libavcodec     54. 92.100 / 54. 92.100
  libavformat    54. 63.103 / 54. 63.103
  libavdevice    54.  3.103 / 54.  3.103
  libavfilter     3. 42.103 /  3. 42.103
  libswscale      2.  2.100 /  2.  2.100
  libswresample   0. 17.102 /  0. 17.102
  libpostproc    52.  2.100 / 52.  2.100
[ogg @ 0x961d5c0] Multiple fisbone for the same stream is not implemented. Update your FFmpeg version to the newest one from Git. If the problem still occurs, it means that your file has a feature which has not been implemented.
[ogg @ 0x961d5c0] Header parsing failed for stream 0
[ogg @ 0x961d5c0] Broken file, keyframe not correctly marked.
Input #0, ogg, from 'test.ogv':
  Duration: 00:27:43.67, start: 0.000000, bitrate: 998 kb/s
    Stream #0:0: Data: none
    Stream #0:1: Video: theora, yuv420p, 1280x800 [SAR 1:1 DAR 8:5], 15 fps, 15 tbr, 15 tbn, 15 tbc
    Metadata:
      RECORDMYDESKTOP : 0.3.8.1
    Stream #0:2: Audio: vorbis, 22050 Hz, mono, fltp, 89 kb/s
Output #0, avi, to 'test_2_pass.avi':
  Metadata:
    ISFT            : Lavf54.63.103
    Stream #0:0: Video: mpeg4 (FMP4 / 0x34504D46), yuv420p, 1280x800 [SAR 1:1 DAR 8:5], q=2-31, 200 kb/s, 15 tbn, 15 tbc
    Metadata:
      RECORDMYDESKTOP : 0.3.8.1
    Stream #0:1: Audio: mp3 (U[0][0][0] / 0x0055), 22050 Hz, mono, fltp
Stream mapping:
  Stream #0:1 -> #0:0 (theora -> mpeg4)
  Stream #0:2 -> #0:1 (vorbis -> libmp3lame)
Press [q] to stop, [?] for help
[ogg @ 0x961d5c0] Broken file, keyframe not correctly marked.
    Last message repeated 1 times
Broken file, keyframe not correctly marked.ime=00:00:09.84 bitrate= 348.1kbits/s    
Broken file, keyframe not correctly marked.time=00:00:15.80 bitrate= 425.4kbits/s    
Broken file, keyframe not correctly marked.time=00:00:23.86 bitrate= 449.4kbits/s    
[ogg @ 0x961d5c0] Broken file, keyframe not correctly marked.
Broken file, keyframe not correctly marked.time=00:00:31.94 bitrate= 426.5kbits/s    
Broken file, keyframe not correctly marked.time=00:00:35.86 bitrate= 452.9kbits/s    
Broken file, keyframe not correctly marked.time=00:00:42.21 bitrate= 512.3kbits/s    
Broken file, keyframe not correctly marked.time=00:00:53.66 bitrate= 525.3kbits/s    
Broken file, keyframe not correctly marked.time=00:00:59.42 bitrate= 518.7kbits/s    
Broken file, keyframe not correctly marked.time=00:01:03.39 bitrate= 522.0kbits/s    
[ogg @ 0x961d5c0] Broken file, keyframe not correctly marked.
Broken file, keyframe not correctly marked.time=00:01:16.27 bitrate= 538.7kbits/s    
Broken file, keyframe not correctly marked.time=00:01:19.20 bitrate= 553.6kbits/s    
Broken file, keyframe not correctly marked.time=00:01:24.71 bitrate= 549.8kbits/s    
[ogg @ 0x961d5c0] Broken file, keyframe not correctly marked.
Broken file, keyframe not correctly marked.time=00:01:30.26 bitrate= 543.5kbits/s    
Broken file, keyframe not correctly marked.time=00:01:37.22 bitrate= 536.0kbits/s    
[ogg @ 0x961d5c0] Broken file, keyframe not correctly marked.
Broken file, keyframe not correctly marked.time=00:01:43.28 bitrate= 529.9kbits/s    
Broken file, keyframe not correctly marked.time=00:01:47.33 bitrate= 535.1kbits/s    
[ogg @ 0x961d5c0] Broken file, keyframe not correctly marked.
Broken file, keyframe not correctly marked.time=00:01:56.32 bitrate= 516.3kbits/s    
Broken file, keyframe not correctly marked.time=00:02:07.50 bitrate= 514.0kbits/s    
Broken file, keyframe not correctly marked.time=00:02:11.66 bitrate= 520.0kbits/s    
[ogg @ 0x961d5c0] Broken file, keyframe not correctly marked.
Broken file, keyframe not correctly marked.time=00:02:19.73 bitrate= 508.7kbits/s    
Broken file, keyframe not correctly marked.time=00:02:24.87 bitrate= 510.0kbits/s    
Broken file, keyframe not correctly marked.time=00:02:33.93 bitrate= 514.3kbits/s    
Broken file, keyframe not correctly marked.time=00:02:38.33 bitrate= 520.0kbits/s    
Broken file, keyframe not correctly marked.time=00:02:45.06 bitrate= 533.8kbits/s    
Broken file, keyframe not correctly marked.time=00:02:48.00 bitrate= 543.0kbits/s    
Broken file, keyframe not correctly marked.time=00:02:57.73 bitrate= 561.0kbits/s    
Broken file, keyframe not correctly marked.time=00:03:02.51 bitrate= 562.9kbits/s    
[ogg @ 0x961d5c0] Broken file, keyframe not correctly marked.
Broken file, keyframe not correctly marked.time=00:03:11.58 bitrate= 561.5kbits/s    
Broken file, keyframe not correctly marked.time=00:03:14.00 bitrate= 566.5kbits/s    
Broken file, keyframe not correctly marked.time=00:03:18.68 bitrate= 565.3kbits/s    
Broken file, keyframe not correctly marked.time=00:03:21.93 bitrate= 564.6kbits/s    
Broken file, keyframe not correctly marked.time=00:03:31.26 bitrate= 557.7kbits/s    
Broken file, keyframe not correctly marked.time=00:03:34.93 bitrate= 557.5kbits/s    
[ogg @ 0x961d5c0] Broken file, keyframe not correctly marked.
Broken file, keyframe not correctly marked.time=00:03:44.54 bitrate= 539.3kbits/s    
Broken file, keyframe not correctly marked.time=00:03:48.20 bitrate= 539.0kbits/s    
Broken file, keyframe not correctly marked.time=00:03:51.46 bitrate= 540.2kbits/s    
Broken file, keyframe not correctly marked.time=00:04:01.80 bitrate= 541.0kbits/s    
Broken file, keyframe not correctly marked.time=00:04:06.09 bitrate= 537.9kbits/s    
Broken file, keyframe not correctly marked.time=00:04:09.02 bitrate= 539.1kbits/s    
Broken file, keyframe not correctly marked.time=00:04:12.40 bitrate= 538.0kbits/s    
Broken file, keyframe not correctly marked.time=00:04:17.56 bitrate= 535.2kbits/s    
Broken file, keyframe not correctly marked.time=00:04:28.66 bitrate= 533.4kbits/s    
Broken file, keyframe not correctly marked.time=00:04:32.40 bitrate= 533.4kbits/s    
[ogg @ 0x961d5c0] Broken file, keyframe not correctly marked.
Broken file, keyframe not correctly marked.time=00:04:43.01 bitrate= 523.9kbits/s    
[ogg @ 0x961d5c0] Broken file, keyframe not correctly marked.
Broken file, keyframe not correctly marked.time=00:04:55.26 bitrate= 519.7kbits/s    
Broken file, keyframe not correctly marked.time=00:05:02.73 bitrate= 511.6kbits/s    
[ogg @ 0x961d5c0] Broken file, keyframe not correctly marked.
Broken file, keyframe not correctly marked.time=00:05:08.33 bitrate= 507.0kbits/s    
Broken file, keyframe not correctly marked.time=00:05:11.46 bitrate= 508.4kbits/s    
Broken file, keyframe not correctly marked.time=00:05:19.73 bitrate= 500.7kbits/s    
[ogg @ 0x961d5c0] Broken file, keyframe not correctly marked.
Broken file, keyframe not correctly marked.time=00:05:24.80 bitrate= 498.3kbits/s    
Broken file, keyframe not correctly marked.time=00:05:29.24 bitrate= 497.5kbits/s    
Broken file, keyframe not correctly marked.time=00:05:38.40 bitrate= 494.8kbits/s    
Broken file, keyframe not correctly marked.time=00:05:44.00 bitrate= 491.2kbits/s    
Broken file, keyframe not correctly marked.time=00:05:53.06 bitrate= 488.7kbits/s    
[ogg @ 0x961d5c0] Broken file, keyframe not correctly marked.
Broken file, keyframe not correctly marked.time=00:06:02.26 bitrate= 484.3kbits/s    
Broken file, keyframe not correctly marked.time=00:06:05.46 bitrate= 483.5kbits/s    
Broken file, keyframe not correctly marked.time=00:06:16.99 bitrate= 477.5kbits/s    
Broken file, keyframe not correctly marked.time=00:06:22.00 bitrate= 475.4kbits/s    
Broken file, keyframe not correctly marked.time=00:06:25.13 bitrate= 479.8kbits/s    
Broken file, keyframe not correctly marked.time=00:06:31.91 bitrate= 487.2kbits/s    
Broken file, keyframe not correctly marked.time=00:06:39.20 bitrate= 493.6kbits/s    
Broken file, keyframe not correctly marked.time=00:06:42.62 bitrate= 497.3kbits/s    
Broken file, keyframe not correctly marked.time=00:06:45.60 bitrate= 500.5kbits/s    
Broken file, keyframe not correctly marked.time=00:06:52.13 bitrate= 499.3kbits/s    
Broken file, keyframe not correctly marked.time=00:06:59.73 bitrate= 504.4kbits/s    
Broken file, keyframe not correctly marked.time=00:07:12.77 bitrate= 516.9kbits/s    
Broken file, keyframe not correctly marked.time=00:07:16.50 bitrate= 519.3kbits/s    
Broken file, keyframe not correctly marked.time=00:07:27.47 bitrate= 526.4kbits/s    
Broken file, keyframe not correctly marked.time=00:07:29.66 bitrate= 529.6kbits/s    
Broken file, keyframe not correctly marked.time=00:07:32.93 bitrate= 532.9kbits/s    
Broken file, keyframe not correctly marked.time=00:07:38.20 bitrate= 532.6kbits/s    
Broken file, keyframe not correctly marked.time=00:07:43.46 bitrate= 532.2kbits/s    
Broken file, keyframe not correctly marked.time=00:07:49.08 bitrate= 531.6kbits/s    
[ogg @ 0x961d5c0] Broken file, keyframe not correctly marked.
Broken file, keyframe not correctly marked.time=00:08:01.12 bitrate= 536.7kbits/s    
Broken file, keyframe not correctly marked.time=00:08:04.80 bitrate= 536.9kbits/s    
Broken file, keyframe not correctly marked.time=00:08:08.48 bitrate= 537.8kbits/s    
Broken file, keyframe not correctly marked.time=00:08:12.17 bitrate= 538.1kbits/s    
Broken file, keyframe not correctly marked.time=00:08:15.67 bitrate= 539.2kbits/s    
Broken file, keyframe not correctly marked.time=00:08:22.26 bitrate= 541.3kbits/s    
Broken file, keyframe not correctly marked.time=00:08:25.20 bitrate= 542.4kbits/s    
Broken file, keyframe not correctly marked.time=00:08:35.94 bitrate= 545.2kbits/s    
Broken file, keyframe not correctly marked.time=00:08:38.93 bitrate= 545.8kbits/s    
Broken file, keyframe not correctly marked.time=00:08:43.12 bitrate= 545.8kbits/s    
Broken file, keyframe not correctly marked.time=00:08:48.66 bitrate= 543.9kbits/s    
Broken file, keyframe not correctly marked.time=00:08:52.68 bitrate= 543.9kbits/s    
Broken file, keyframe not correctly marked.time=00:09:00.33 bitrate= 545.2kbits/s    
Broken file, keyframe not correctly marked.time=00:09:05.26 bitrate= 544.3kbits/s    
Broken file, keyframe not correctly marked.time=00:09:09.53 bitrate= 544.0kbits/s    
Broken file, keyframe not correctly marked.time=00:09:12.93 bitrate= 544.5kbits/s    
Broken file, keyframe not correctly marked.time=00:09:18.73 bitrate= 550.2kbits/s    
Broken file, keyframe not correctly marked.time=00:09:21.94 bitrate= 552.0kbits/s    
Broken file, keyframe not correctly marked.time=00:09:24.40 bitrate= 554.4kbits/s    
Broken file, keyframe not correctly marked.time=00:09:31.14 bitrate= 559.3kbits/s    
Broken file, keyframe not correctly marked.time=00:09:34.58 bitrate= 560.7kbits/s    
Broken file, keyframe not correctly marked.time=00:09:38.26 bitrate= 562.0kbits/s    
Broken file, keyframe not correctly marked.time=00:09:42.42 bitrate= 562.9kbits/s    
Broken file, keyframe not correctly marked.time=00:09:52.58 bitrate= 568.4kbits/s    
[ogg @ 0x961d5c0] Broken file, keyframe not correctly marked.
Broken file, keyframe not correctly marked.time=00:10:01.33 bitrate= 567.9kbits/s    
Broken file, keyframe not correctly marked.time=00:10:04.20 bitrate= 567.4kbits/s    
Broken file, keyframe not correctly marked.time=00:10:08.33 bitrate= 566.3kbits/s    
Broken file, keyframe not correctly marked.time=00:10:17.53 bitrate= 563.1kbits/s    
[ogg @ 0x961d5c0] Broken file, keyframe not correctly marked.
Broken file, keyframe not correctly marked.time=00:10:26.59 bitrate= 557.3kbits/s    
Broken file, keyframe not correctly marked.time=00:10:29.06 bitrate= 557.9kbits/s    
Broken file, keyframe not correctly marked.time=00:10:34.59 bitrate= 555.3kbits/s    
Broken file, keyframe not correctly marked.time=00:10:46.20 bitrate= 552.9kbits/s    
Broken file, keyframe not correctly marked.time=00:10:50.86 bitrate= 551.8kbits/s    
Broken file, keyframe not correctly marked.time=00:10:57.94 bitrate= 548.5kbits/s    
Broken file, keyframe not correctly marked.time=00:11:01.73 bitrate= 547.5kbits/s    
[ogg @ 0x961d5c0] Broken file, keyframe not correctly marked.
Broken file, keyframe not correctly marked.time=00:11:11.24 bitrate= 542.0kbits/s    
Broken file, keyframe not correctly marked.time=00:11:17.26 bitrate= 541.7kbits/s    
Broken file, keyframe not correctly marked.time=00:11:21.00 bitrate= 541.3kbits/s    
Broken file, keyframe not correctly marked.time=00:11:25.87 bitrate= 539.5kbits/s    
Broken file, keyframe not correctly marked.time=00:11:39.50 bitrate= 536.7kbits/s    
Broken file, keyframe not correctly marked.time=00:11:43.46 bitrate= 535.8kbits/s    
Broken file, keyframe not correctly marked.time=00:11:50.68 bitrate= 535.5kbits/s    
Broken file, keyframe not correctly marked.time=00:12:00.73 bitrate= 535.7kbits/s    
Broken file, keyframe not correctly marked.time=00:12:04.95 bitrate= 534.8kbits/s    
Broken file, keyframe not correctly marked.time=00:12:08.06 bitrate= 534.8kbits/s    
Broken file, keyframe not correctly marked.time=00:12:12.13 bitrate= 534.5kbits/s    
Broken file, keyframe not correctly marked.time=00:12:15.55 bitrate= 534.8kbits/s    
Broken file, keyframe not correctly marked.time=00:12:19.36 bitrate= 534.4kbits/s    
[ogg @ 0x961d5c0] Broken file, keyframe not correctly marked.
Broken file, keyframe not correctly marked.time=00:12:28.30 bitrate= 530.2kbits/s    
Broken file, keyframe not correctly marked.time=00:12:34.93 bitrate= 528.6kbits/s    
Broken file, keyframe not correctly marked.time=00:12:40.11 bitrate= 527.1kbits/s    
[ogg @ 0x961d5c0] Broken file, keyframe not correctly marked.
Broken file, keyframe not correctly marked.time=00:12:56.20 bitrate= 522.7kbits/s    
[ogg @ 0x961d5c0] Broken file, keyframe not correctly marked.
Broken file, keyframe not correctly marked.time=00:13:04.53 bitrate= 518.7kbits/s    
[ogg @ 0x961d5c0] Broken file, keyframe not correctly marked.
Broken file, keyframe not correctly marked.time=00:13:12.13 bitrate= 519.9kbits/s    
Broken file, keyframe not correctly marked.time=00:13:14.95 bitrate= 521.2kbits/s    
Broken file, keyframe not correctly marked.time=00:13:25.20 bitrate= 524.3kbits/s    
Broken file, keyframe not correctly marked.time=00:13:34.40 bitrate= 528.2kbits/s    
Broken file, keyframe not correctly marked.time=00:13:41.60 bitrate= 531.3kbits/s    
Broken file, keyframe not correctly marked.time=00:13:51.79 bitrate= 534.5kbits/s    
Broken file, keyframe not correctly marked.time=00:13:55.03 bitrate= 535.9kbits/s    
Broken file, keyframe not correctly marked.time=00:13:58.19 bitrate= 536.7kbits/s    
Broken file, keyframe not correctly marked.time=00:14:03.41 bitrate= 539.8kbits/s    
Broken file, keyframe not correctly marked.time=00:14:13.00 bitrate= 541.4kbits/s    
Broken file, keyframe not correctly marked.time=00:14:17.60 bitrate= 541.6kbits/s    
Broken file, keyframe not correctly marked.time=00:14:23.47 bitrate= 539.8kbits/s    
Broken file, keyframe not correctly marked.time=00:14:28.70 bitrate= 538.9kbits/s    
Broken file, keyframe not correctly marked.time=00:14:32.00 bitrate= 538.7kbits/s    
Broken file, keyframe not correctly marked.time=00:14:38.53 bitrate= 538.9kbits/s    
Broken file, keyframe not correctly marked.time=00:14:44.08 bitrate= 539.6kbits/s    
Broken file, keyframe not correctly marked.time=00:14:47.84 bitrate= 539.1kbits/s    
Broken file, keyframe not correctly marked.time=00:14:58.60 bitrate= 539.0kbits/s    
Broken file, keyframe not correctly marked.time=00:15:08.61 bitrate= 537.9kbits/s    
Broken file, keyframe not correctly marked.time=00:15:12.71 bitrate= 537.2kbits/s    
Broken file, keyframe not correctly marked.time=00:15:15.20 bitrate= 537.5kbits/s    
Broken file, keyframe not correctly marked.time=00:15:18.60 bitrate= 537.3kbits/s    
Broken file, keyframe not correctly marked.time=00:15:31.13 bitrate= 537.0kbits/s    
Broken file, keyframe not correctly marked.time=00:15:38.37 bitrate= 536.5kbits/s    
[ogg @ 0x961d5c0] Broken file, keyframe not correctly marked.
Broken file, keyframe not correctly marked.time=00:15:45.73 bitrate= 535.8kbits/s    
Broken file, keyframe not correctly marked.time=00:15:53.60 bitrate= 536.6kbits/s    
Broken file, keyframe not correctly marked.time=00:16:06.53 bitrate= 537.3kbits/s    
Broken file, keyframe not correctly marked.time=00:16:12.26 bitrate= 538.1kbits/s    
Broken file, keyframe not correctly marked.time=00:16:14.93 bitrate= 538.4kbits/s    
Broken file, keyframe not correctly marked.time=00:16:18.20 bitrate= 538.8kbits/s    
Broken file, keyframe not correctly marked.time=00:16:24.73 bitrate= 539.1kbits/s    
Broken file, keyframe not correctly marked.time=00:16:29.06 bitrate= 539.0kbits/s    
Broken file, keyframe not correctly marked.time=00:16:32.13 bitrate= 539.6kbits/s    
Broken file, keyframe not correctly marked.time=00:16:35.60 bitrate= 539.4kbits/s    
Broken file, keyframe not correctly marked.time=00:16:42.16 bitrate= 540.3kbits/s    
Broken file, keyframe not correctly marked.time=00:16:46.02 bitrate= 540.0kbits/s    
Broken file, keyframe not correctly marked.time=00:16:48.87 bitrate= 540.2kbits/s    
Broken file, keyframe not correctly marked.time=00:16:52.06 bitrate= 540.6kbits/s    
Broken file, keyframe not correctly marked.time=00:16:59.53 bitrate= 540.2kbits/s    
[ogg @ 0x961d5c0] Broken file, keyframe not correctly marked.
Broken file, keyframe not correctly marked.time=00:17:07.66 bitrate= 540.0kbits/s    
Broken file, keyframe not correctly marked.time=00:17:11.20 bitrate= 539.8kbits/s    
Broken file, keyframe not correctly marked.time=00:17:13.66 bitrate= 540.5kbits/s    
Broken file, keyframe not correctly marked.time=00:17:17.16 bitrate= 540.7kbits/s    
Broken file, keyframe not correctly marked.time=00:17:24.80 bitrate= 540.2kbits/s    
Broken file, keyframe not correctly marked.time=00:17:28.76 bitrate= 539.8kbits/s    
Broken file, keyframe not correctly marked.time=00:17:41.13 bitrate= 539.7kbits/s    
Broken file, keyframe not correctly marked.time=00:17:44.75 bitrate= 539.6kbits/s    
Broken file, keyframe not correctly marked.time=00:17:59.27 bitrate= 542.5kbits/s    
[ogg @ 0x961d5c0] Broken file, keyframe not correctly marked.
Broken file, keyframe not correctly marked.time=00:18:08.36 bitrate= 540.8kbits/s    
Broken file, keyframe not correctly marked.time=00:18:12.00 bitrate= 540.7kbits/s    
Broken file, keyframe not correctly marked.time=00:18:14.53 bitrate= 541.2kbits/s    
Broken file, keyframe not correctly marked.time=00:18:20.32 bitrate= 540.0kbits/s    
Broken file, keyframe not correctly marked.time=00:18:37.33 bitrate= 539.7kbits/s    
Broken file, keyframe not correctly marked.time=00:18:40.46 bitrate= 539.8kbits/s    
Broken file, keyframe not correctly marked.time=00:18:45.61 bitrate= 540.1kbits/s    
Broken file, keyframe not correctly marked.time=00:18:53.13 bitrate= 546.1kbits/s    
Broken file, keyframe not correctly marked.time=00:18:59.01 bitrate= 548.6kbits/s    
Broken file, keyframe not correctly marked.time=00:19:06.77 bitrate= 551.9kbits/s    
Broken file, keyframe not correctly marked.time=00:19:11.71 bitrate= 551.5kbits/s    
Broken file, keyframe not correctly marked.time=00:19:14.35 bitrate= 552.8kbits/s    
Broken file, keyframe not correctly marked.time=00:19:17.25 bitrate= 553.3kbits/s    
[ogg @ 0x961d5c0] Broken file, keyframe not correctly marked.
Broken file, keyframe not correctly marked.time=00:19:24.86 bitrate= 551.1kbits/s    
Broken file, keyframe not correctly marked.time=00:19:29.00 bitrate= 550.9kbits/s    
Broken file, keyframe not correctly marked.time=00:19:37.23 bitrate= 548.3kbits/s    
Broken file, keyframe not correctly marked.time=00:19:41.60 bitrate= 548.1kbits/s    
[ogg @ 0x961d5c0] Broken file, keyframe not correctly marked.
Broken file, keyframe not correctly marked.time=00:19:49.22 bitrate= 547.5kbits/s    
Broken file, keyframe not correctly marked.time=00:19:54.39 bitrate= 546.9kbits/s    
[ogg @ 0x961d5c0] Broken file, keyframe not correctly marked.
Broken file, keyframe not correctly marked.time=00:19:59.13 bitrate= 547.0kbits/s    
Broken file, keyframe not correctly marked.time=00:20:06.86 bitrate= 546.6kbits/s    
Broken file, keyframe not correctly marked.time=00:20:14.01 bitrate= 551.6kbits/s    
Broken file, keyframe not correctly marked.time=00:20:19.97 bitrate= 553.1kbits/s    
Broken file, keyframe not correctly marked.time=00:20:22.86 bitrate= 555.4kbits/s    
Broken file, keyframe not correctly marked.time=00:20:26.81 bitrate= 555.2kbits/s    
Broken file, keyframe not correctly marked.time=00:20:29.00 bitrate= 555.3kbits/s    
Broken file, keyframe not correctly marked.time=00:20:34.31 bitrate= 554.9kbits/s    
Broken file, keyframe not correctly marked.time=00:20:38.00 bitrate= 554.3kbits/s    
Broken file, keyframe not correctly marked.time=00:20:45.36 bitrate= 553.2kbits/s    
Broken file, keyframe not correctly marked.time=00:20:48.88 bitrate= 552.7kbits/s    
Broken file, keyframe not correctly marked.time=00:20:58.10 bitrate= 551.7kbits/s    
Broken file, keyframe not correctly marked.time=00:21:02.80 bitrate= 551.4kbits/s    
Broken file, keyframe not correctly marked.time=00:21:05.86 bitrate= 550.9kbits/s    
Broken file, keyframe not correctly marked.time=00:21:15.53 bitrate= 550.8kbits/s    
Broken file, keyframe not correctly marked.time=00:21:18.27 bitrate= 550.5kbits/s    
Broken file, keyframe not correctly marked.time=00:21:23.26 bitrate= 550.4kbits/s    
Broken file, keyframe not correctly marked.time=00:21:28.12 bitrate= 549.8kbits/s    
Broken file, keyframe not correctly marked.time=00:21:32.66 bitrate= 548.6kbits/s    
Broken file, keyframe not correctly marked.time=00:21:35.86 bitrate= 548.1kbits/s    
Broken file, keyframe not correctly marked.time=00:21:40.45 bitrate= 548.0kbits/s    
Broken file, keyframe not correctly marked.time=00:21:44.45 bitrate= 548.0kbits/s    
Broken file, keyframe not correctly marked.time=00:21:48.06 bitrate= 547.2kbits/s    
Broken file, keyframe not correctly marked.time=00:21:58.26 bitrate= 547.1kbits/s    
Broken file, keyframe not correctly marked.time=00:22:15.33 bitrate= 547.5kbits/s    
Broken file, keyframe not correctly marked.time=00:22:19.46 bitrate= 548.2kbits/s    
Broken file, keyframe not correctly marked.time=00:22:22.24 bitrate= 548.6kbits/s    
Broken file, keyframe not correctly marked.time=00:22:26.20 bitrate= 548.5kbits/s    
Broken file, keyframe not correctly marked.time=00:22:32.33 bitrate= 549.1kbits/s    
Broken file, keyframe not correctly marked.time=00:22:35.40 bitrate= 549.4kbits/s    
Broken file, keyframe not correctly marked.time=00:22:38.40 bitrate= 549.9kbits/s    
Broken file, keyframe not correctly marked.time=00:22:52.60 bitrate= 550.3kbits/s    
Broken file, keyframe not correctly marked.time=00:23:00.86 bitrate= 552.0kbits/s    
Broken file, keyframe not correctly marked.time=00:23:06.00 bitrate= 551.4kbits/s    
Broken file, keyframe not correctly marked.time=00:23:10.80 bitrate= 552.5kbits/s    
Broken file, keyframe not correctly marked.time=00:23:16.95 bitrate= 552.3kbits/s    
Broken file, keyframe not correctly marked.time=00:23:21.06 bitrate= 551.7kbits/s    
Broken file, keyframe not correctly marked.time=00:23:24.00 bitrate= 551.9kbits/s    
Broken file, keyframe not correctly marked.time=00:23:29.20 bitrate= 550.8kbits/s    
Broken file, keyframe not correctly marked.time=00:23:33.69 bitrate= 550.1kbits/s    
Broken file, keyframe not correctly marked.time=00:23:40.26 bitrate= 549.5kbits/s    
Broken file, keyframe not correctly marked.time=00:23:42.40 bitrate= 549.6kbits/s    
Broken file, keyframe not correctly marked.time=00:23:47.82 bitrate= 549.7kbits/s    
Broken file, keyframe not correctly marked.time=00:23:56.13 bitrate= 551.2kbits/s    
Broken file, keyframe not correctly marked.time=00:24:01.93 bitrate= 549.0kbits/s    
Broken file, keyframe not correctly marked.time=00:24:05.80 bitrate= 547.6kbits/s    
[ogg @ 0x961d5c0] Broken file, keyframe not correctly marked.
Broken file, keyframe not correctly marked.time=00:24:10.60 bitrate= 545.7kbits/s    
[ogg @ 0x961d5c0] Broken file, keyframe not correctly marked.
    Last message repeated 1 times
Broken file, keyframe not correctly marked.time=00:24:24.00 bitrate= 540.8kbits/s    
Broken file, keyframe not correctly marked.time=00:24:29.73 bitrate= 538.6kbits/s    
Broken file, keyframe not correctly marked.time=00:24:40.33 bitrate= 534.8kbits/s    
Broken file, keyframe not correctly marked.time=00:24:44.60 bitrate= 533.3kbits/s    
Broken file, keyframe not correctly marked.time=00:24:52.80 bitrate= 530.3kbits/s    
Broken file, keyframe not correctly marked.time=00:25:00.60 bitrate= 527.6kbits/s    
Broken file, keyframe not correctly marked.time=00:25:09.46 bitrate= 524.5kbits/s    
[ogg @ 0x961d5c0] Broken file, keyframe not correctly marked.
Broken file, keyframe not correctly marked.time=00:25:18.33 bitrate= 521.4kbits/s    
Broken file, keyframe not correctly marked.time=00:25:26.26 bitrate= 518.7kbits/s    
Broken file, keyframe not correctly marked.time=00:25:29.33 bitrate= 517.7kbits/s    
Broken file, keyframe not correctly marked.time=00:25:34.60 bitrate= 515.9kbits/s    
Broken file, keyframe not correctly marked.time=00:25:38.66 bitrate= 514.5kbits/s    
Broken file, keyframe not correctly marked.time=00:25:42.80 bitrate= 513.1kbits/s    
Broken file, keyframe not correctly marked.time=00:25:48.13 bitrate= 511.4kbits/s    
Broken file, keyframe not correctly marked.time=00:25:53.80 bitrate= 509.5kbits/s    
Broken file, keyframe not correctly marked.time=00:26:05.46 bitrate= 505.7kbits/s    
Broken file, keyframe not correctly marked.time=00:26:12.53 bitrate= 503.4kbits/s    
[ogg @ 0x961d5c0] Broken file, keyframe not correctly marked.
Broken file, keyframe not correctly marked.time=00:26:19.26 bitrate= 501.3kbits/s    
Broken file, keyframe not correctly marked.time=00:26:27.53 bitrate= 498.7kbits/s    
Broken file, keyframe not correctly marked.time=00:26:33.00 bitrate= 497.0kbits/s    
Broken file, keyframe not correctly marked.time=00:26:39.06 bitrate= 495.1kbits/s    
[ogg @ 0x961d5c0] Broken file, keyframe not correctly marked.
Broken file, keyframe not correctly marked.time=00:26:48.86 bitrate= 492.1kbits/s    
Broken file, keyframe not correctly marked.time=00:26:56.93 bitrate= 489.6kbits/s    
[ogg @ 0x961d5c0] Broken file, keyframe not correctly marked.
Broken file, keyframe not correctly marked.time=00:27:00.66 bitrate= 488.5kbits/s    
Broken file, keyframe not correctly marked.time=00:27:06.66 bitrate= 486.7kbits/s    
Broken file, keyframe not correctly marked.time=00:27:17.40 bitrate= 483.5kbits/s    
Broken file, keyframe not correctly marked.time=00:27:21.73 bitrate= 482.2kbits/s    
Broken file, keyframe not correctly marked.time=00:27:27.13 bitrate= 480.6kbits/s    
Broken file, keyframe not correctly marked.time=00:27:31.26 bitrate= 479.4kbits/s    
Broken file, keyframe not correctly marked.time=00:27:35.66 bitrate= 478.2kbits/s    
frame=16698 fps= 76 q=31.0 Lsize=  109158kB time=00:27:43.66 bitrate= 537.5kbits/s    
video:101633kB audio:5608kB subtitle:0 global headers:0kB muxing overhead 1.787581%
```
This actually works but the quality of the .avi file is very low (too low).

Has anyone an idea on how to procead ?

Jacques

---

### Post by andrew.46 on 2013-03-09
I am not familiar with kdenlive but I believe you do not have to convert to avi to create a suitable input file. Looks like there is a reasonable range of input formats to chose from:

[http://www.kdenlive.org/about-kdenlive/audio-and-video-formats](http://www.kdenlive.org/about-kdenlive/audio-and-video-formats)

Looks like it supports mp4 container and vorbis audio (which means you should be able to simply copy your audio stream). Not sure about the video stream, perhaps you will have to wait for somebody with kdenlive experience...

**Edit: **I would imagine a* lossless *video codec would be the go if kdenlive will not import theora.

---

### Post by Jacques Duflos on 2013-03-10
Hi Andrew,
You are right, KDEnLive can handle a lot of formats, except .ogv. All I want is to encode my .ogv videos into any other format without loosing quality and without skipping identical frames.

[QUOTE=andrew.46]**Edit: **I would imagine a* lossless *video codec would be the go if kdenlive will not import theora.         [/QUOTE]
I have been looking on the ffmpeg man page, but I did not find how to use this lossless codec. Could you be more explicit ?

---

### Post by andrew.46 on 2013-03-10
Perhaps something like:

```

ffmpeg -i test.ogv -c:a copy -c:v huffyuv test.avi

```

This will be a big file but hopefully kdenlive can then import the file and you can convert, edit etc. Did not realise that huffyuv will not live in mp4 container, looks like mkv and avi, curious...

---

### Post by Jacques Duflos on 2013-03-12
I've tried this line and I obtained the reverse effect (the video rate was ok but the audio was way too fast).
So I just deleted the -v:a copy and it worked fine (I am not convinced by what I did...)!

17 Gb for 25 a minute video :shock: :shock: :shock: :shock: :shock:
As you said, it IS the heck of a big file !!

But it did work.
Thanks a lot, Andrew !
Here is the video by the way : [https://vimeo.com/61588508](https://vimeo.com/61588508)

Edit : Why can't I show this thread as resolved ?

---

### Post by andrew.46 on 2013-03-12
Good to hear that the issue is resolved, perhaps there is a more elegant way to resolve it but sounds like it is working anyway :). Concerning the Thread Solved thing, I believe there is a but with the new Forums setup still being worked at...

---

