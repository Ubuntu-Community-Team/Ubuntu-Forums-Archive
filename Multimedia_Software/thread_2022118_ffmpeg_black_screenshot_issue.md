---
title: "ffmpeg black screenshot issue"
date: 2012-07-10
forum: Multimedia Software
---

### Post by Artifaxx616 on 2012-07-10
I recently installed ffmpeg and other software according to this guide: [http://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide](http://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide)

Whenever I use the following command (or any similar command) to take a screenshot of a file, I end up with a 6kB black screenshot:

ffmpeg -ss 120 -i input.mkv -vframes 1 -f image2 pic.png

Is there another codec I need?

Also, I'm using Ubuntu 11.10 64-bit.

---

### Post by Artifaxx616 on 2012-07-10
Also, this seems to only happen on .mkv files. Taking a screenshot of a m2ts file works perfectly.

---

### Post by FakeOutdoorsman on 2012-07-10
Can you show the complete console output of the command that gives you a black image? Did you try a different *-ss* value? Does it work if you use *-ss* as an output option (past *-i input*)?

---

### Post by Artifaxx616 on 2012-07-10
working/path# ffmpeg -ss 600 -i Blade.Trinity.Unrated.2004.BluRay.1080p.h264.DTS-HD.MA.Remux-HiFi.mkv -vframes 1 -f image2 test.png
ffmpeg version 0.11.1.git Copyright (c) 2000-2012 the FFmpeg developers
  built on Jul 10 2012 16:08:21 with gcc 4.6.1
  configuration: --enable-gpl --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-nonfree --enable-version3
  libavutil      51. 64.100 / 51. 64.100
  libavcodec     54. 33.100 / 54. 33.100
  libavformat    54. 15.102 / 54. 15.102
  libavdevice    54.  1.100 / 54.  1.100
  libavfilter     3.  1.100 /  3.  1.100
  libswscale      2.  1.100 /  2.  1.100
  libswresample   0. 15.100 /  0. 15.100
  libpostproc    52.  0.100 / 52.  0.100
[dca @ 0x170f2a0] Number of channels changed in DCA decoder (6 -> 7)
Input #0, matroska,webm, from 'Blade.Trinity.Unrated.2004.BluRay.1080p.h264.DTS-HD.MA.Remux-HiFi.mkv':
  Metadata:
    title           : Blade.Trinity.Unrated.2004.BluRay.1080p.h264.DTS-HD.MA.Remux-HiFi
    creation_time   : 2012-07-10 00:50:50
  Duration: 02:02:21.76, start: 0.000000, bitrate: 34035 kb/s
    Chapter #0.0: start 0.000000, end 407.407000
    Metadata:
      title           : 00:00:00.000
    Chapter #0.1: start 407.407000, end 779.362000
    Metadata:
      title           : 00:06:47.407
    Chapter #0.2: start 779.362000, end 1036.077000
    Metadata:
      title           : 00:12:59.362
    Chapter #0.3: start 1036.077000, end 1128.419000
    Metadata:
      title           : 00:17:16.077
    Chapter #0.4: start 1128.419000, end 1368.284000
    Metadata:
      title           : 00:18:48.419
    Chapter #0.5: start 1368.284000, end 1625.624000
    Metadata:
      title           : 00:22:48.284
    Chapter #0.6: start 1625.624000, end 2062.894000
    Metadata:
      title           : 00:27:05.624
    Chapter #0.7: start 2062.894000, end 2467.674000
    Metadata:
      title           : 00:34:22.894
    Chapter #0.8: start 2467.674000, end 2740.905000
    Metadata:
      title           : 00:41:07.674
    Chapter #0.9: start 2740.905000, end 3055.886000
    Metadata:
      title           : 00:45:40.905
    Chapter #0.10: start 3055.886000, end 3250.747000
    Metadata:
      title           : 00:50:55.886
    Chapter #0.11: start 3250.747000, end 3488.026000
    Metadata:
      title           : 00:54:10.747
    Chapter #0.12: start 3488.026000, end 4085.164000
    Metadata:
      title           : 00:58:08.026
    Chapter #0.13: start 4085.164000, end 4674.712000
    Metadata:
      title           : 01:08:05.164
    Chapter #0.14: start 4674.712000, end 4919.915000
    Metadata:
      title           : 01:17:54.712
    Chapter #0.15: start 4919.915000, end 5312.057000
    Metadata:
      title           : 01:21:59.915
    Chapter #0.16: start 5312.057000, end 5610.230000
    Metadata:
      title           : 01:28:32.057
    Chapter #0.17: start 5610.230000, end 6091.711000
    Metadata:
      title           : 01:33:30.230
    Chapter #0.18: start 6091.711000, end 6373.158000
    Metadata:
      title           : 01:41:31.711
    Chapter #0.19: start 6373.158000, end 6645.013000
    Metadata:
      title           : 01:46:13.158
    Chapter #0.20: start 6645.013000, end 6831.992000
    Metadata:
      title           : 01:50:45.013
    Chapter #0.21: start 6831.992000, end 7341.760000
    Metadata:
      title           : 01:53:51.992
    Stream #0:0(eng): Video: h264 (High), yuv420p, 1920x1080 [SAR 1:1 DAR 16:9], 23.98 fps, 23.98 tbr, 1k tbn, 47.95 tbc (default)
    Stream #0:1(eng): Audio: dts (DTS-HD MA), 48000 Hz, 6.1, s16, 1536 kb/s (default)
    Metadata:
      title           : DTS-HD Master Audio English 5.1
    Stream #0:2(cze): Subtitle: hdmv_pgs_subtitle (default)
    Stream #0:3(eng): Subtitle: hdmv_pgs_subtitle
    Stream #0:4(ger): Subtitle: hdmv_pgs_subtitle
    Stream #0:5(spa): Subtitle: hdmv_pgs_subtitle
[graph 0 input from stream 0:0 @ 0x1725a80] w:1920 h:1080 pixfmt:yuv420p tb:1/1000 fr:24000/1001 sar:1/1 sws_param:flags=2
[output stream 0:0 @ 0x1725ae0] No opaque field provided
[auto-inserted scaler 0 @ 0x17264e0] w:1920 h:1080 fmt:yuv420p sar:1/1 -> w:1920 h:1080 fmt:rgb24 sar:1/1 flags:0x4
Output #0, image2, to 'test.png':
  Metadata:
    title           : Blade.Trinity.Unrated.2004.BluRay.1080p.h264.DTS-HD.MA.Remux-HiFi
    encoder         : Lavf54.15.102
    Chapter #0.0: start 0.000000, end 179.362000
    Metadata:
      title           : 00:06:47.407
    Chapter #0.1: start 179.362000, end 436.077000
    Metadata:
      title           : 00:12:59.362
    Chapter #0.2: start 436.077000, end 528.419000
    Metadata:
      title           : 00:17:16.077
    Chapter #0.3: start 528.419000, end 768.284000
    Metadata:
      title           : 00:18:48.419
    Chapter #0.4: start 768.284000, end 1025.624000
    Metadata:
      title           : 00:22:48.284
    Chapter #0.5: start 1025.624000, end 1462.894000
    Metadata:
      title           : 00:27:05.624
    Chapter #0.6: start 1462.894000, end 1867.674000
    Metadata:
      title           : 00:34:22.894
    Chapter #0.7: start 1867.674000, end 2140.905000
    Metadata:
      title           : 00:41:07.674
    Chapter #0.8: start 2140.905000, end 2455.886000
    Metadata:
      title           : 00:45:40.905
    Chapter #0.9: start 2455.886000, end 2650.747000
    Metadata:
      title           : 00:50:55.886
    Chapter #0.10: start 2650.747000, end 2888.026000
    Metadata:
      title           : 00:54:10.747
    Chapter #0.11: start 2888.026000, end 3485.164000
    Metadata:
      title           : 00:58:08.026
    Chapter #0.12: start 3485.164000, end 4074.712000
    Metadata:
      title           : 01:08:05.164
    Chapter #0.13: start 4074.712000, end 4319.915000
    Metadata:
      title           : 01:17:54.712
    Chapter #0.14: start 4319.915000, end 4712.057000
    Metadata:
      title           : 01:21:59.915
    Chapter #0.15: start 4712.057000, end 5010.230000
    Metadata:
      title           : 01:28:32.057
    Chapter #0.16: start 5010.230000, end 5491.711000
    Metadata:
      title           : 01:33:30.230
    Chapter #0.17: start 5491.711000, end 5773.158000
    Metadata:
      title           : 01:41:31.711
    Chapter #0.18: start 5773.158000, end 6045.013000
    Metadata:
      title           : 01:46:13.158
    Chapter #0.19: start 6045.013000, end 6231.992000
    Metadata:
      title           : 01:50:45.013
    Chapter #0.20: start 6231.992000, end 6741.760000
    Metadata:
      title           : 01:53:51.992
    Stream #0:0(eng): Video: png, rgb24, 1920x1080 [SAR 1:1 DAR 16:9], q=2-31, 200 kb/s, 90k tbn, 23.98 tbc (default)
Stream mapping:
  Stream #0:0 -> #0:0 (h264 -> png)
Press [q] to stop, [?] for help
DTS -600000, next:-708 st:0 invalid dropping
PTS -599958, next:-708 invalid dropping st:0
DTS -599958, next:40292 st:0 invalid dropping
PTS -599917, next:40292 invalid dropping st:0
DTS -599917, next:81292 st:0 invalid dropping
PTS -599875, next:81292 invalid dropping st:0
DTS -599875, next:122292 st:0 invalid dropping
PTS -599833, next:122292 invalid dropping st:0
DTS -599833, next:163292 st:0 invalid dropping
PTS -599791, next:163292 invalid dropping st:0
frame=    1 fps=0.0 q=0.0 Lsize=       0kB time=00:00:00.04 bitrate=   0.0kbits/s dup=0 drop=6
video:6kB audio:0kB subtitle:0 global headers:0kB muxing overhead -100.000000%
working/path#

---

