---
title: "ffmpeg coredumps when recording X11 desktop"
date: 2009-10-05
forum: Multimedia Software
---

### Post by Lars Noodén on 2009-10-05
I've tried several settings for bitrate (-b) and group of pictures size (-g), including leaving them blank for the default.  The options I've tried all end in a segmentation fault and core dump after a few seconds.

Is there a known work-around for recording a hi-res desktop to video?

```
$ [B]ffmpeg -f x11grab -vc theora -s 1600x1050 \
   -r 24 -b 1200 -g 300 -i :0.0 /tmp/screenCapture1.ogv[/B]
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Aug 26 2009 09:45:20, gcc: 4.4.1
[x11grab @ 0x21eeab0]device: :0.0 -> display: :0.0 x: 0 y: 0 width: 1600 height: 1050
[x11grab @ 0x21eeab0]shared memory extension  found
Input #0, x11grab, from ':0.0':
  Duration: N/A, start: 1254762985.555098, bitrate: 1290240 kb/s
    Stream #0.0: Video: rawvideo, rgb32, 1600x1050, 1290240 kb/s, 24 tbr, 1000k tbn, 24 tbc
Output #0, ogg, to '/tmp/screenCapture1.ogv':
    Stream #0.0: Video: libtheora, yuv420p, 1600x1050, q=2-31, 1 kb/s, 90k tbn, 24 tbc
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
Segmentation fault (core dumped)    447kB time=9.42 bitrate= 389.1kbits/s

```

---

### Post by FakeOutdoorsman on 2009-10-05
> **Lars Noodén said:**
> I've tried several settings for bitrate (-b) and group of pictures size (-g), including leaving them blank for the default.  The options I've tried all end in a segmentation fault and core dump after a few seconds.

Is there a known work-around for recording a hi-res desktop to video?

```
ffmpeg -f x11grab -vc theora -s 1600x1050 \
   -r 24 -b 1200 -g 300 -i :0.0 /tmp/screenCapture1.ogv
The *-b* option takes a value in bits/s, so you need to add a "k": -b 1200k.  This is probably the cause of the crash.  Also the option **-vc theora** is not valid.  You probably meant **-vcodec libtheora**.

Try this:
[code]ffmpeg -r 30 -s 1600x1050 -f x11grab -i :0.0 -g 300 -threads 0 -vcodec libx264 -vpre fastfirstpass -vpre baseline -sc_threshold -1 -cqp 22 -flags -loop planet_of_the_apes_the_musical.mp4
```

You may have to mess around with the size option, *-s*.  My ancient computer can only record at around 9 fps with this at 800x600, but the quality is nice.  Also, you will need to enable restricted encoders in FFmpeg.  Karmic users can install the **libavcodec-extra-52** package.

---

### Post by Lars Noodén on 2009-10-06
This will get it a few more frames before it coredumps.  
ffmpeg didn't accept the options -vpre fastfirstpass and -vpre baseline

What would restricted encoders have to do with theora?

```

$ [b]ffmpeg -v 2 -y -s 1600x1050 -r 9 -f x11grab -i :0.0 \
  -g 300 -threads 0 -vcodec libtheora -sc_threshold -1 \
  -cqp 22  -b 1200k  /tmp/screenCapture1.ogv[/b]
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Aug 26 2009 09:45:20, gcc: 4.4.1
[x11grab @ 0x12cca60]device: :0.0 -> display: :0.0 x: 0 y: 0 width: 1600 height: 1050
[x11grab @ 0x12cca60]shared memory extension  found
Input #0, x11grab, from ':0.0':
  Duration: N/A, start: 1254834662.893646, bitrate: 483840 kb/s
    Stream #0.0, 1/1000000: Video: rawvideo, rgb32, 1600x1050, 1/9, 483840 kb/s, 9 tbr, 1000k tbn, 9 tbc
Output #0, ogg, to '/tmp/screenCapture1.ogv':
    Stream #0.0, 1/90000: Video: libtheora, yuv420p, 1600x1050, 1/9, q=2-31, 1200 kb/s, 90k tbn, 9 tbc
Stream mapping:
  Stream #0.0 -> #0.0
[ogg @ 0x12d9f70]theora kfgshift 9, vrev 1
Press [q] to stop encoding
frame=    3 fps=  0 q=0.0 size=     208kB time=0.33 bitrate=5123.2kbits/s dup=2 dframe=   13 fps=  7 q=0.0 size=     408kB time=1.44 bitrate=2313.2kbits/s dup=12 frame=   17 fps=  7 q=0.0 size=     455kB time=1.89 bitrate=1972.4kbits/s dup=16 frame=   26 fps=  8 q=0.0 size=     598kB time=2.89 bitrate=1696.5kbits/s dup=25 frame=   33 fps=  8 q=0.0 size=     724kB time=3.67 bitrate=1616.6kbits/s dup=32 frame=   39 fps=  9 q=0.0 size=     813kB time=4.33 bitrate=1536.3kbits/s dup=38 Segmentation fault (core dumped)

```

---

### Post by FakeOutdoorsman on 2009-10-06
> **Lars Noodén said:**
> This will get it a few more frames before it coredumps.  
ffmpeg didn't accept the options -vpre fastfirstpass and -vpre baseline

Did you install the **libavcodec-extra-52** package?  You need that to encode with libx264.

> **Lars Noodén said:**
> What would restricted encoders have to do with theora?

Nothing at all because libtheora is not restricted.  However, it would allow you to use libx264 and its presets as it is a restricted encoder.

---

### Post by Lars Noodén on 2009-10-12
> **FakeOutdoorsman said:**
> Did you install the **libavcodec-extra-52** package?  You need that to encode with libx264.



Nothing at all because libtheora is not restricted.  However, it would allow you to use libx264 and its presets as it is a restricted encoder.

What would be the reason for using libx64 and its presets?  
I'd prefer to find a way around using restricted items.

---

### Post by FakeOutdoorsman on 2009-10-12
> **Lars Noodén said:**
> What would be the reason for using libx64 and its presets?

Using libx264 would generally result in a better quality video at equivalent bitrates, not including any (other) lossless formats.

---

