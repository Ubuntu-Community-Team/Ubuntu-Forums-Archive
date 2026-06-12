---
title: "Mencoder tacks on extra time to video"
date: 2010-05-13
forum: Multimedia Software
---

### Post by RudiePoo on 2010-05-13
I've been at this for a couple days now and haven't really gotten anywhere... I'm running 10.04 and I recorded a video using RecordMyDesktop.  I was hoping to be able to upload it straight to YouTube like I remember doing in the past, but during the conversion from .ogv to flv the colors of the video become smeared which renders it unwatchable.  After a bit of searching the web it looked like converting the file from .ogv to .avi with Mencoder was the solution.  However, after being converted it now has about seven minutes of nothing tacked onto the end making the video 10:36 instead of the original length of 3:31.  So far converting the file with Mencoder has been the only conversion that does not render the video unwatchable because of the colors being smeared; every other converter I've used (ffmpeg, AVS... and couple more I can't remember) does this.  Any help will be much appreciated.

**Mencoder Output**
```
mencoder ~/Videos/G51-27.ogv -o myvideo.avi -ovc lavc -oac mp3lame
MEncoder SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
success: format: 0  data: 0x0 - 0x1a175b3
Ogg stream 0 is of an unknown type
[Ogg] stream 1: video (Theora v3.2.1), -vid 0
[Ogg] stream 2: audio (Vorbis), -aid 0
Ogg file format detected.
VIDEO:  [theo]  1440x896  24bpp  15.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:18  fourcc:0x6F656874  size:1440x896  fps:15.000  ftime:=0.0667
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 22050 Hz, 1 ch, s16le, 90.0 kbit/25.51% (ratio: 11248->44100)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis)
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[theora @ 0x896f320]Missing extradata!
Could not open codec.
VDecoder init failed :(
Opening video decoder: [theora] Theora/VP3
VDec: vo config request - 1440 x 896 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.61:1 - prescaling to correct movie aspect.
videocodec: libavcodec (1440x896 fourcc=34504d46 [FMP4])
Selected video codec: [theora] vfm: theora (Theora (free, reworked VP3))
==========================================================================
MP3 audio selected.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Pos: 212.0s   3180f (100%) 67.15fps Trem:   0min  13mb  A-V:0.082 [453:89]
Invalid frame duration value (212.067/0.000 => -212.067). Defaulting to 0.067 sec.
Pos: 212.1s   3181f (100%) 67.15fps Trem:   0min  13mb  A-V:0.080 [453:89]
3180 duplicate frame(s)!
Pos: 424.1s   3182f (100%) 67.11fps Trem:   0min  13mb  A-V:0.020 [226:89]
3182 duplicate frame(s)!
Pos: 636.3s   3183f (100%) 67.08fps Trem:   0min  13mb  A-V:21.240 [151:89]
Flushing video frames.
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream:  151.126 kbit/s  (18890 B/s)  size: 12020832 bytes  636.333 secs  3183 frames

Audio stream:   89.024 kbit/s  (11127 B/s)  size: 2357500 bytes  211.853 secs
```

---

### Post by LuridCinema on 2010-05-13
I have resolved encoding problems in ffmpeg where it would not convert from one format to another by first simply having ffmpeg go from title1.ogv to title2.ogv. That way ffmpeg writes whatever it needs to determine time. THEN I will encode to another format or splice, etc

---

### Post by RudiePoo on 2010-05-13
Thanks for the reply.  I gave it a shot, but I'm still getting the smeared colors after converting it.  The length of the video is accurate though :)

**ffmpeg output**
```
ffmpeg -i ~/Videos/G51-27.ogv G51-27_1.ogv
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3
Input #0, ogg, from '/home/rudiepoo/Videos/G51-27.ogv':
  Duration: 00:03:32.20, start: 0.000000, bitrate: 1031 kb/s
    Stream #0.0: Invalid Codec type -1
    Stream #0.1: Video: theora, yuv420p, 1440x896, PAR 1:1 DAR 45:28, 15 tbr, 15 tbn, 15 tbc
    Stream #0.2: Audio: vorbis, 22050 Hz, mono, s16, 89 kb/s
Output #0, ogg, to 'G51-27_1.ogv':
    Stream #0.0: Video: libtheora, yuv420p, 1440x896 [PAR 1:1 DAR 45:28], q=2-31, 200 kb/s, 90k tbn, 15 tbc
    Stream #0.1: Audio: flac, 22050 Hz, mono, s16, 64 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.2 -> #0.1
Press [q] to stop encoding
frame= 3180 fps=  8 q=0.0 Lsize=   10369kB time=157.80 bitrate= 538.3kbits/s    
video:5037kB audio:5171kB global headers:3kB muxing overhead 1.551807%
```

---

### Post by RudiePoo on 2010-05-14
I tried converting it with Mencoder and then using Keno cut out the extra seven minutes, but then rendering it screws up the colors again...

---

