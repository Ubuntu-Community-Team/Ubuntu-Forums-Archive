---
title: "Cannot convert to ogv with ffmpeg on Ubuntu 10.04"
date: 2010-05-18
forum: Multimedia Software
---

### Post by skatebiker on 2010-05-18
The command line to convert to ogg theora

ffmpeg -y -i input.flv -sameq OUTPUT.ogv

runs perfectly on 9.04 but on 10.04 it gives errors:

```

ffmpeg -y -i input.flv -sameq OUTPUT.ogv
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
Input #0, flv, from 'input.flv':
  Duration: 00:01:00.93, start: 0.000000, bitrate: 445 kb/s
    Stream #0.0: Video: flv, yuv420p, 480x360, 389 kb/s, 15 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 22050 Hz, mono, s16, 56 kb/s
Output #0, ogg, to 'OUTPUT.ogv':
    Stream #0.0: Video: libtheora, yuv420p, 480x360, q=2-31, 200 kb/s, 90k tbn, 15 tbc
    Stream #0.1: Audio: flac, 22050 Hz, mono, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[libtheora @ 0x82a9720]theora_encode_init failed
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height


```

---

### Post by skatebiker on 2010-05-19
Does really nobody know this ?

---

### Post by skatebiker on 2010-05-21
Really nobody knows thia ?

---

### Post by andrew.46 on 2010-05-21
Hi skatebiker,

> **skatebiker said:**
> Really nobody knows this ?

Perhaps try:

```
ffmpeg -i input.flv -b 400k ***[COLOR="Red"]-r 25[/COLOR]*** OUTPUT.ogv
```

Andrew

---

### Post by truman11_au on 2010-05-22
> **andrew.46 said:**
> 

Perhaps try:

```
ffmpeg -i input.flv -b 400k ***[COLOR=Red]-r 25[/COLOR]*** OUTPUT.ogv
```Andrew


I was having the same problem, what worked for me was manually setting the height x width to maintain the original aspect ratio:

```
ffmpeg -y -i input.flv -sameq [COLOR=Red]-s [/COLOR][FONT=monospace][COLOR=Red]480x360[/COLOR] [/FONT]OUTPUT.ogv
```

Dion

---

### Post by d3v1150m471c on 2010-05-22
does
```

ffmpeg -i ~/video.flv ~/output.ogv

```not work?

---

### Post by andrew.46 on 2010-05-22
Hi Dion,

> **truman11_au said:**
> I was having the same problem, what worked for me was manually setting the height x width to maintain the original aspect ratio

Mind you if you look at the output settings with the original command:

```
Output #0, ogg, to 'OUTPUT.ogv':
    Stream #0.0: Video: libtheora, yuv420p, **[COLOR="Red"]480x360[/COLOR]**, q=2-31, 200 kb/s, 90k tbn, 15 tbc
    Stream #0.1: Audio: flac, 22050 Hz, mono, s16, 64 kb/s
```

it looks as if FFmpeg has already found and incorporated those settings...

Andrew

---

### Post by truman11_au on 2010-05-22
> **andrew.46 said:**
> Hi Dion,

it looks as if FFmpeg has already found and incorporated those settings...

Andrew

Good point, and looking back at my own situation i didn't end up using what was reported there.

This didn't work:

```
ffmpeg -i input.flv output.ogv

Seems stream 0 codec frame rate differs from container frame rate: 59.83 (29917/500) -> 59.75 (239/4)
Input #0, flv, from 'input.flv':
  Duration: 00:06:17.37, start: 0.000000, bitrate: 820 kb/s
    Stream #0.0: Video: h264, yuv420p, 640x360 [PAR 1:1 DAR 16:9], 820 kb/s, 59.75 tbr, 1k tbn, 59.83 tbc
    Stream #0.1: Audio: aac, 44100 Hz, mono, s16
Output #0, ogg, to 'output.ogv':
    Stream #0.0: Video: libtheora, yuv420p, 640x360 [PAR 1:1 DAR 16:9], q=2-31, 200 kb/s, 90k tbn, 59.75 tbc
    Stream #0.1: Audio: flac, 44100 Hz, mono, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[libtheora @ 0x885c670]theora_encode_init failed
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height
```

But this did:

```

ffmpeg -i input.flv -s 640x320 ouput.ogv

Seems stream 0 codec frame rate differs from container frame rate: 59.83 (29917/500) -> 59.75 (239/4)
Input #0, flv, from 'input.flv':
  Duration: 00:06:17.37, start: 0.000000, bitrate: 820 kb/s
    Stream #0.0: Video: h264, yuv420p, 640x360 [PAR 1:1 DAR 16:9], 820 kb/s, 59.75 tbr, 1k tbn, 59.83 tbc
    Stream #0.1: Audio: aac, 44100 Hz, mono, s16
Output #0, ogg, to 'ouput.ogv':
    Stream #0.0: Video: libtheora, yuv420p, 640x320 [PAR 8:9 DAR 16:9], q=2-31, 200 kb/s, 90k tbn, 59.75 tbc
    Stream #0.1: Audio: flac, 44100 Hz, mono, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
frame=   14 fps=  0 q=0.0 Lsize=       4kB time=0.03 bitrate= 951.5kbits/s    
video:0kB audio:0kB global headers:3kB muxing overhead 8.919289%

^C Received signal 2: terminating.
```

Maybe you could shed some further light?

Dion

---

### Post by andrew.46 on 2010-05-22
Hi Dion,

> **truman11_au said:**
> Maybe you could shed some further light?

I am only guessing but it looks as if there are some limitations in dimensions for theora transcoding with FFmpeg, in a similar way to h263 transcoding. It would be nice to know exactly what those limitations are mind you... Anybody?

Andrew

---

### Post by gervin23 on 2010-07-02
i just experienced this oddity myself and according to [libtheora internals]("http://www.theora.org/doc/libtheora-1.0/structth__info.html#6b1adc3a16a8336a72692b0a5937214c") the height and width must be a multiple of 16.

---

### Post by zhangweiwu on 2010-08-26
I got the same problem when trying to scale down 1280x720 video to 640x360, and ends up having to scale to 512x288 instead. The limitation that video size must be a factor of 16 do not make me feel too constrained at all, but I don't appreciate that libtheora / ffmpeg didn't say anything nor try to round it up nor offer suggestion. It would be better to see improvements on this direction.

---

### Post by yevgeni on 2011-10-06
This still hasn't been resolved as of now. Time to download the source code and help out!

---

