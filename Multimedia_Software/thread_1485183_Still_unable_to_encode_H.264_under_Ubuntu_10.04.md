---
title: "Still unable to encode H.264 under Ubuntu 10.04"
date: 2010-05-16
forum: Multimedia Software
---

### Post by skatebiker on 2010-05-16
After several google searches and forum searches, installing restricted repos, encoders, codecs, ffmpec still REFUSES to encode H.264.

Here the output of an FLV to be converted:


```

 ffmpeg -i fumehood.flv -vcodec libx264  x.mp4
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

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 15.00 (15/1)
Input #0, flv, from 'fumehood.flv':
  Duration: 00:01:00.93, start: 0.000000, bitrate: 445 kb/s
    Stream #0.0: Video: flv, yuv420p, 480x360, 389 kb/s, 15 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 22050 Hz, mono, s16, 56 kb/s
Output #0, mp4, to 'x.mp4':
    Stream #0.0: Video: libx264, yuv420p, 480x360, q=2-31, 200 kb/s, 90k tbn, 15 tbc
    Stream #0.1: Audio: libfaac, 22050 Hz, mono, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[libx264 @ 0x992b700]broken ffmpeg default settings detected
[libx264 @ 0x992b700]use an encoding preset (vpre)
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height


```

libx264 is installed.
What is the problem here ?
It seems that Ubuntu 10.04 does not support this format anymore.

---

### Post by vkcaspervk on 2010-05-16
When you don't include the video options for encoding it tried to pull a preset, which I think are broken by default.

Are you by chance encoding for iphone usage? If you are this should help ya.
Here is the script Ive been using that works quite well. Its a 2 pass (takes longer better quality) I build my own ffmpeg and x264, if you have trouble let me know and I will post the script I use to update and build my ffmpeg and libfaac.

note: If you have a single core, dual core. Update the "-threads 4" to how many you have. =)
```

#!/bin/sh

voptions="-r 30000/1001 -s 480x320 -aspect 16:9 -vcodec libx264 -b 512k -bt 1024k -maxrate 4M \
-flags +loop -cmp +chroma -me_range 16 -g 300 -keyint_min 25 -sc_threshold 40 -i_qfactor 0.71 \
-rc_eq \"blurCplx^(1-qComp)\" -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -coder 0 -refs 1 -bufsize 4M \
-level 21 -partitions parti4x4+partp8x8+partb8x8 -subq 5 -f mp4"

aoptions="-acodec libfaac -ac 2 -ar 44100 -ab 128k "

ffmpeg -y -i "$1" -threads 4 $voptions -pass 1 -an "$2.mp4"
ffmpeg -y -i "$1" -threads 4 $voptions -pass 2 $aoptions "$2.mp4"
rm *.log
rm *.mbtree

```

---

### Post by skatebiker on 2010-05-16
No it's for making a video for a <video> html tag. BTW I found that this long command line 
```

ffmpeg -i input.flv -acodec libfaac -vcodec libx264 -ac 2 -ab 128k -vpre hq -vpre ipod320 -crf 26 -threads 0 output.mp4

```
does work, as it is shown in the <video> tag in Chrome but not in Firefox 3.6.

I don't know whether this is because either my vidoe is not real h264 *or* Firefox does not support the <video> tag with h.264.

---

### Post by vkcaspervk on 2010-05-16
Ah, the <video> tag is still quite new, after a little googling...

IE really doesn't support it yet [COLOR=Red]* correct me if Im wrong.[/COLOR]

Firefox3.5+ only supports : MPEG4, OGG
[https://developer.mozilla.org/En/HTML/Element/Video](https://developer.mozilla.org/En/HTML/Element/Video)

Safari only supports x264.

Chrome is shipping all the above.

If its an active public server, might be best to let html5 work out the kinks before using it. 
If its private then pick your browser of choice and encode to match. =)

PS Funny that snippet you posted, is telling ffmpeg to use -threads 0... =x

---

### Post by FakeOutdoorsman on 2010-05-17
> **vkcaspervk said:**
> Ah, the <video> tag is still quite new, after a little googling...

IE really doesn't support it yet [COLOR=Red]* correct me if Im wrong.[/COLOR]

Firefox3.5+ only supports : MPEG4, OGG
[https://developer.mozilla.org/En/HTML/Element/Video](https://developer.mozilla.org/En/HTML/Element/Video)

Safari only supports x264.

Chrome is shipping all the above.

If its an active public server, might be best to let html5 work out the kinks before using it. 
If its private then pick your browser of choice and encode to match. =)

PS Funny that snippet you posted, is telling ffmpeg to use -threads 0... =x

Wikipedia chart of [HTML5 video browser support](http://en.wikipedia.org/wiki/HTML5_video#Browser_support).  The option **-threads 0** allows *libx264* to automatically determine an appropriate number of threads.  It does not mean "use zero threads".

---

### Post by vkcaspervk on 2010-05-17
> **FakeOutdoorsman said:**
> Wikipedia chart of [HTML5 video browser support]("http://en.wikipedia.org/wiki/HTML5_video#Browser_support").  The option **-threads 0** allows *libx264* to automatically determine an appropriate number of threads.  It does not mean "use zero threads".

Humour isn't your strong point is it?! I see you are a master Googler...

---

