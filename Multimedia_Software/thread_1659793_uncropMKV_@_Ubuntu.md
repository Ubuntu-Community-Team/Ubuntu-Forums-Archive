---
title: "uncropMKV @ Ubuntu"
date: 2011-01-04
forum: Multimedia Software
---

### Post by IP-Sh0k on 2011-01-04
Hello folks,

there is a program calles uncropMKV for windows. It uses avisynth and some other tools to uncrop MKV files.
So i can change my mkv files by tsmuxer to a bluray an burn it.
uncropMKV uncrops the videofile, because the most mkv files are cinescope or 1920x800 pixel.
TsMuxer needs a resolution of 1920x1080. so how can i add those black bars on top and bottom of the videofile to reach this resolution, or how can i run uncropMKV (i tried wine, but it doesnt work right now)?

Some guys told me to try avidemux, but i dont know how to handle this programm for mkv h264 containers/files.

PLEASE help me as soon as possible

thank you

---

### Post by IP-Sh0k on 2011-01-05
okay i got it with avidemux.

Now i take the output format mpeg4-avc an delete each audiosource to add it later again.

But i think there is a loss of quality in the default settings of h264 in avidemux.
How can i set the Framerate to 23.976 and High@4.1 in avidemux and minimize the loss of quality?

---

### Post by IP-Sh0k on 2011-01-06
Okay i got it ... it was a format problem with the audio codec.. 
deaktivating the audio worked perfectly..

but another question. 
What is a good Quantiser value?... standard is 26... but i think there is a loss of quality...
now im experimenting with this value...

is there someone with experience?

Thanks

---

### Post by FakeOutdoorsman on 2011-01-06
You can use FFmpeg to add padding to the video. The following example is for a more recent FFmpeg than what is currently in the repository (as of Ubuntu Maverick Meerkat 10.10). This command also just copies the audio so there is no audio re-encoding:
```
ffmpeg -i input -vcodec libx264 -vpre medium -crf 22 -threads 0 -vf pad=0:1080:0:140 -acodec copy output.mp4
```
If you are using an older FFmpeg then try (untested by me):
```
ffmpeg -i input -vcodec libx264 -vpre medium -crf 22 -threads 0 -padtop 140 -padbottom 140 -acodec copy output.mp4
```
Decrease the crf value until you get a quality you like. You can use the *-t* option to encode a section of the video so you don't have to wait for the whole thing which is useful for testing.

See the [FFmpeg x264 Encoding Guide](http://rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/) for more info.

---

### Post by IP-Sh0k on 2011-01-07
yes thank you.. but there is a problem... can i deaktivate the sound for reauthoring?

because with sound there is only: 
```
ip-sh0k@ipsh0k:~/Downloads/Iron Man/Iron.Man.2.German.DL.1080p.BluRay.x264-EXQUiSiTE$ ffmpeg -i exq-iron.man.2-1080p.mkv -vcodec libx264 -vpre medium -crf 22 -threads 0 -vf pad=0:1080:0:140 -acodec copy output.mp4
FFmpeg version SVN-r26215, Copyright (c) 2000-2011 the FFmpeg developers
  built on Jan  4 2011 21:16:37 with gcc 4.4.5
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50.36. 0 / 50.36. 0
  libavcore      0.16. 0 /  0.16. 0
  libavcodec    52.102. 0 / 52.102. 0
  libavformat   52.92. 0 / 52.92. 0
  libavdevice   52. 2. 2 / 52. 2. 2
  libavfilter    1.72. 0 /  1.72. 0
  libswscale     0.12. 0 /  0.12. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[matroska,webm @ 0x2c0e550] max_analyze_duration reached
[matroska,webm @ 0x2c0e550] Estimating duration from bitrate, this may be inaccurate

Seems stream 0 codec frame rate differs from container frame rate: 47.95 (20000000/417083) -> 23.98 (24000/1001)
Input #0, matroska,webm, from 'exq-iron.man.2-1080p.mkv':
  Duration: 02:04:50.47, start: 0.000000, bitrate: 3072 kb/s
    Chapter #0.0: start 0.000000, end 318.318000
    Metadata:
      title           : 00:00:00.000
    Chapter #0.1: start 318.318000, end 681.723000
    Metadata:
      title           : 00:05:18.318
    Chapter #0.2: start 681.723000, end 1093.926000
    Metadata:
      title           : 00:11:21.723
    Chapter #0.3: start 1093.926000, end 1567.024000
    Metadata:
      title           : 00:18:13.926
    Chapter #0.4: start 1567.024000, end 1840.797000
    Metadata:
      title           : 00:26:07.024
    Chapter #0.5: start 1840.797000, end 2267.015000
    Metadata:
      title           : 00:30:40.797
    Chapter #0.6: start 2267.015000, end 2654.277000
    Metadata:
      title           : 00:37:47.015
    Chapter #0.7: start 2654.277000, end 3113.360000
    Metadata:
      title           : 00:44:14.277
    Chapter #0.8: start 3113.360000, end 3624.830000
    Metadata:
      title           : 00:51:53.360
    Chapter #0.9: start 3624.830000, end 4035.531000
    Metadata:
      title           : 01:00:24.830
    Chapter #0.10: start 4035.531000, end 4574.779000
    Metadata:
      title           : 01:07:15.531
    Chapter #0.11: start 4574.779000, end 4887.299000
    Metadata:
      title           : 01:16:14.779
    Chapter #0.12: start 4887.299000, end 5447.567000
    Metadata:
      title           : 01:21:27.299
    Chapter #0.13: start 5447.567000, end 5943.354000
    Metadata:
      title           : 01:30:47.567
    Chapter #0.14: start 5943.354000, end 6355.808000
    Metadata:
      title           : 01:39:03.354
    Chapter #0.15: start 6355.808000, end 6872.199000
    Metadata:
      title           : 01:45:55.808
    Chapter #0.16: start 6872.199000, end 7036.571000
    Metadata:
      title           : 01:54:32.199
    Chapter #0.17: start 7036.571000, end 7490.477000
    Metadata:
      title           : 01:57:16.571
    Stream #0.0(eng): Video: h264, yuv420p, 1920x816 [PAR 1:1 DAR 40:17], 23.98 fps, 23.98 tbr, 1k tbn, 47.95 tbc
    Stream #0.1(ger): Audio: dca, 48000 Hz, 5.1, s16, 1536 kb/s
    Metadata:
      title           : German DTS 1510kbps
    Stream #0.2(eng): Audio: dca, 48000 Hz, 5.1, s16, 1536 kb/s
    Metadata:
      title           : English DTS 1510kbps
    Stream #0.3(ger): Subtitle: [0][0][0][0] / 0x0000
    Metadata:
      title           : German Forced
File 'output.mp4' already exists. Overwrite ? [y/N] y
[buffer @ 0x2db2d90] w:1920 h:816 pixfmt:yuv420p
[pad @ 0x2d4d920] w:1920 h:1080 x:0 y:140 color:0x108080FF[yuva]
[libx264 @ 0x2fb88f0] using SAR=1/1
[libx264 @ 0x2fb88f0] using cpu capabilities: MMX2 SSE2Fast SSSE3 Cache64
[libx264 @ 0x2fb88f0] profile High, level 4.0
[libx264 @ 0x2fb88f0] 264 - core 112 r1834 a51816a - H.264/MPEG-4 AVC codec - Copyleft 2003-2010 - http://www.videolan.org/x264.html - options: cabac=1 ref=3 deblock=1:0:0 analyse=0x3:0x113 me=hex subme=7 psy=1 psy_rd=1.00:0.00 mixed_ref=1 me_range=16 chroma_me=1 trellis=1 8x8dct=1 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=-2 threads=6 sliced_threads=0 nr=0 decimate=1 interlaced=0 constrained_intra=0 bframes=3 b_pyramid=2 b_adapt=1 b_bias=0 direct=1 weightb=1 open_gop=0 weightp=2 keyint=250 keyint_min=25 scenecut=40 intra_refresh=0 rc_lookahead=40 rc=crf mbtree=1 crf=22.0 qcomp=0.60 qpmin=10 qpmax=51 qpstep=4 ip_ratio=1.41 aq=1:1.00
[mp4 @ 0x2c8eff0] track 1: could not find tag, codec not currently supported in container
Output #0, mp4, to 'output.mp4':
  Metadata:
    encoder         : Lavf52.92.0
    Chapter #0.0: start 0.000000, end 318.318000
    Metadata:
      title           : 00:00:00.000
    Chapter #0.1: start 318.318000, end 681.723000
    Metadata:
      title           : 00:05:18.318
    Chapter #0.2: start 681.723000, end 1093.926000
    Metadata:
      title           : 00:11:21.723
    Chapter #0.3: start 1093.926000, end 1567.024000
    Metadata:
      title           : 00:18:13.926
    Chapter #0.4: start 1567.024000, end 1840.797000
    Metadata:
      title           : 00:26:07.024
    Chapter #0.5: start 1840.797000, end 2267.015000
    Metadata:
      title           : 00:30:40.797
    Chapter #0.6: start 2267.015000, end 2654.277000
    Metadata:
      title           : 00:37:47.015
    Chapter #0.7: start 2654.277000, end 3113.360000
    Metadata:
      title           : 00:44:14.277
    Chapter #0.8: start 3113.360000, end 3624.830000
    Metadata:
      title           : 00:51:53.360
    Chapter #0.9: start 3624.830000, end 4035.531000
    Metadata:
      title           : 01:00:24.830
    Chapter #0.10: start 4035.531000, end 4574.779000
    Metadata:
      title           : 01:07:15.531
    Chapter #0.11: start 4574.779000, end 4887.299000
    Metadata:
      title           : 01:16:14.779
    Chapter #0.12: start 4887.299000, end 5447.567000
    Metadata:
      title           : 01:21:27.299
    Chapter #0.13: start 5447.567000, end 5943.354000
    Metadata:
      title           : 01:30:47.567
    Chapter #0.14: start 5943.354000, end 6355.808000
    Metadata:
      title           : 01:39:03.354
    Chapter #0.15: start 6355.808000, end 6872.199000
    Metadata:
      title           : 01:45:55.808
    Chapter #0.16: start 6872.199000, end 7036.571000
    Metadata:
      title           : 01:54:32.199
    Chapter #0.17: start 7036.571000, end 7490.477000
    Metadata:
      title           : 01:57:16.571
    Stream #0.0(eng): Video: libx264, yuv420p, 1920x1080 [PAR 1:1 DAR 16:9], q=10-51, 200 kb/s, 24k tbn, 23.98 tbc
    Stream #0.1(ger): Audio: [0][0][0][0] / 0x0000, 48000 Hz, 5.1, 1536 kb/s
    Metadata:
      title           : German DTS 1510kbps
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Could not write header for output file #0 (incorrect codec parameters ?)

```

and i dont need the sound because i can add it later very easily.

tanks again

---

### Post by FakeOutdoorsman on 2011-01-07
The MP4 container may not be able to handle that audio format, so perhaps you can try changing your output to .mkv. If you want to ignore the audio completely then use the *-an* option.

---

