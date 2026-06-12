---
title: "FFMPEG problem"
date: 2010-03-10
forum: Multimedia Software
---

### Post by prodsacnetworking on 2010-03-10
Hi, 

I installed ffmpeg from the svn.

I compiled it with:

>  ./configure --prefix=/usr/local/ffmpeg --enable-shared --enable-gpl --enable-nonfree --enable-libx264 --enable-decoder=mpeg1video --enable-decoder=mpeg2video --enable-decoder=flv --enable-decoder=mpeg4 --enable-decoder=tiff --enable-decoder=cinepak --enable-decoder=ac3 --enable-decoder=mp3 --enable-decoder=mjpeg --enable-decoder=wmv1 --enable-decoder=wmv2 --enable-decoder=wmv3 --enable-decoder=mpegvideo

whe I try to convert a .FLV to an h264 AVI with:

> /usr/local/ffmpeg/bin/ffmpeg -i livestream_1076113.flv -acodec aac -ab 96k -ac 2 -r 15 -vcodec libx264 /data/ftp/MA2/archives_camz/FLV_DONE/livestream_1076113.avi

it says:

> FFmpeg version SVN-r22407, Copyright (c) 2000-2010 the FFmpeg developers
  built on Mar 10 2010 15:34:19 with gcc 4.3.3
  configuration: --prefix=/usr/local/ffmpeg --enable-shared --enable-gpl --enable-nonfree --enable-libx264 --enable-decoder=mpeg1video --enable-decoder=mpeg2video --enable-decoder=flv --enable-decoder=mpeg4 --enable-decoder=tiff --enable-decoder=cinepak --enable-decoder=ac3 --enable-decoder=mp3 --enable-decoder=mjpeg --enable-decoder=wmv1 --enable-decoder=wmv2 --enable-decoder=wmv3 --enable-decoder=mpegvideo
  libavutil     50.11. 0 / 50.11. 0
  libavcodec    52.58. 0 / 52.58. 0
  libavformat   52.55. 0 / 52.55. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0.10. 0 /  0.10. 0
[flv @ 0x94883a0]Estimating duration from bitrate, this may be inaccurate

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 15.00 (15/1)
Input #0, flv, from 'livestream_1076113.flv':
  Metadata:
    duration        : 3551
    videocodecid    : 4
    audiocodecid    : 2
    canSeekToEnd    : false
    createdby       : FMS 3.5
    creationdate    : Thu Feb 11 12:00:30 2010
  Duration: 00:59:10.82, start: 0.000000, bitrate: 48 kb/s
    Stream #0.0: Video: vp6f, yuv420p, 320x240, 15 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 22050 Hz, 1 channels, s16, 48 kb/s
[libx264 @ 0x94dc840]broken ffmpeg default settings detected
[libx264 @ 0x94dc840]use an encoding preset (vpre)
Output #0, avi, to '/data/ftp/MA2/archives_camz/FLV_DONE/livestream_1076113.avi':
    Stream #0.0: Video: libx264, yuv420p, 320x240, q=2-31, 200 kb/s, 90k tbn, 15 tbc
    Stream #0.1: Audio: aac, 22050 Hz, 2 channels, s16, 96 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Error while opening encoder for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height



It works if I convert to MPEG2VIDEO.

Any ideas? Thanks

---

### Post by andrew.46 on 2010-03-11
Hi prodsacnetworking,

FFmpeg wants you to use a preset:

```
[libx264 @ 0x94dc840]broken ffmpeg default settings detected
[libx264 @ 0x94dc840]use an encoding preset (vpre)
```

To do this you could use something like:

```
-vcodec libx264 -vpre slow -crf 22 -threads 0 
```

but you may run into a little trouble trying to pack h264 into an avi container I suspect, mp4 might be a better choice. Can I make a suggestion as well? Some elements of your compilation look a little unusual, you might derive some benefit from looking over Fakeoutdoorsman's excellent FFmpeg guide:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

All the best,

Andrew

---

### Post by prodsacnetworking on 2010-03-11
thanks a lot. I will batch process the one I need to do and I will reinstall with better compilation ;-)

---

