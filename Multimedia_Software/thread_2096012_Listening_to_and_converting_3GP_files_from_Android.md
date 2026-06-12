---
title: "Listening to and converting 3GP files from Android recorder"
date: 2012-12-18
forum: Multimedia Software
---

### Post by ofnuts on 2012-12-18
I have recordings made on an Android phone with the standard voice recorder app. They have  a 3GP extension. I read elswhere that there are likely using the AMR codec and my system has the two AMR codecs (speech and wideband):
```

lrwxrwxrwx 1 root root     26 2010-12-03 02:00 /usr/lib/libopencore-amrnb.so.0 -> libopencore-amrnb.so.0.0.2
-rw-r--r-- 1 root root 202068 2009-09-28 18:08 /usr/lib/libopencore-amrnb.so.0.0.2
lrwxrwxrwx 1 root root     26 2010-12-03 02:00 /usr/lib/libopencore-amrwb.so.0 -> libopencore-amrwb.so.0.0.2
-rw-r--r-- 1 root root  99612 2009-09-28 18:08 /usr/lib/libopencore-amrwb.so.0.0.2

```However this doesn't seem to be sufficient.

VLC says:
```

[COLOR=#000000]VLC does not support the audio or video format "samr"[/COLOR]

```smplayer doesn't play the file and the media info says:
```

Demuxer: lavpref
[COLOR=#000000]Format[/COLOR]:  [COLOR=#000000]samr[/COLOR]
[COLOR=#000000]Bitrate[/COLOR]: [COLOR=#000000]0 kbps[/COLOR]
[COLOR=#000000]Rate[/COLOR]: [COLOR=#000000]8000 Hz[/COLOR]
[COLOR=#000000]Channels: 1[/COLOR]
[COLOR=#000000]Selected codec[/COLOR]: <empty>

```No codec is selected in the codec list (there are AMR wide- and narrow-band codecs listed though). 

If i try to run ffmpeg I get:
```

$>ffmpeg -i recording2031015976.3gpp -f mp3 converted.mp3
FFmpeg version SVN-r0.5.9-4:0.5.9-0ubuntu0.10.04.1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.9-0ubuntu0.10.04.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Jun 12 2012 16:27:34, gcc: 4.4.3
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'recording2031015976.3gpp':
  Duration: 00:01:50.86, start: 0.000000, bitrate: 5 kb/s
    Stream #0.0(eng): Audio: samr / 0x726D6173, 8000 Hz, mono, s16
Output #0, mp3, to 'converted.mp3':
    Stream #0.0(eng): Audio: libmp3lame, 8000 Hz, mono, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Unsupported codec (id=73728) for input stream #0.0

```Any ideas?

---

### Post by ron999 on 2012-12-18
> **ofnuts said:**
> Any ideas?
Hi
Although you have the two amr codecs installed...
It looks as though your FFmpeg has been compiled without amr support.
I would expect it to show "configuration --enable-libopencore-amrnb --enable-libopencore-amrwb"

Probably your SMPlayer/MPlayer and VLC are also compiled without amr support.

Solution is to compile FFmpeg yourself with amr support.


Workaround is to use static build FFmpeg from here ---> [http://ffmpeg.gusari.org/static/]("http://ffmpeg.gusari.org/static/")
```
./ffmpeg -i recording2031015976.3gpp converted.mp3
```

(Latest versions of FFmpeg have built-in amr decoder support, no need for "--enable-libopencore")

---

### Post by ofnuts on 2012-12-18
Worked a treat. Thanks.

---

