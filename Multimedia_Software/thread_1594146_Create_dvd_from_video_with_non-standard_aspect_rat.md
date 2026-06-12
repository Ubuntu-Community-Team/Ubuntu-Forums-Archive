---
title: "Create dvd from video with non-standard aspect ratio"
date: 2010-10-12
forum: Multimedia Software
---

### Post by pssturges on 2010-10-12
Hi,

I'm trying to create a PAL dvd from a source video with a resolution of 1920x800. I'm using ffmpeg to create the dvd compliant mpg file, then dvdauthor to author the dvd. I'm not looking to put any menus or anything fancy on the dvd, just simple autoplay.

The problem is that the best result I can get the video shunk into a 16:9 frame(ie everyone looks tall and skinny!). 

Here is my ffmpeg command:
```
ffmpeg -i test.mkv -f dvd -target pal-dvd -acodec copy -aspect 16:9 -b 5000kb -mbd rd -trellis -mv0 -cmp 0 -subcmp 2 -y test.mpg
```

My xml file for dvdauthor is very simple:

```

<dvdauthor>
    <vmgm />
    <titleset>
        <titles>
            <pgc>
                <vob file="test.mpg" chapters="0:00" />
            </pgc>
        </titles>
    </titleset>
</dvdauthor>
```

Any ideas how I can get it right? I'm willing to try other software if needed.

Cheers
Phil

---

### Post by pssturges on 2010-10-15
Any thoughts?

---

### Post by mc4man on 2010-10-15
Your aspect ratio is more like 2.40:1, though I seem to remember when using with -target .... that ffmpeg would only produce 2.21:1 
(probably my ignorance  or maybe something about the source

Depending on your version of ffmpeg you may want to try -aspect like this

-vf aspect=

Atm here using just -aspect combined with a -target command produces a video where the ratio is based on  the target (ie. for ntsc 1.50, pal 1.25

I'm sure others know better so a bit of a bump.

---

### Post by no2498 on 2010-10-15
is not 1920x800 a 4.3 ratio 
like 640x480 - 1024x780 -1280x960 ?

---

### Post by pssturges on 2010-10-16
Thanks for the replies.

It seems the problem may not be the encode, but dvdauthor. I changed my ffmpeg command to:

```
ffmpeg -i test.mkv -f dvd -target pal-dvd -acodec copy -aspect 16:9 -b 5000kb -mbd rd -trellis -mv0 -cmp 0 -subcmp 2 -y test.mpg
```

When I play test.mpg it looks correct. The output from "ffmpeg -i test.mpg" is as follows:

```

FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-pthreads --enable-libogg --enable-liba52 --enable-dc1394 --enable-libgsm --disable-debug --enable-libmp3lame --enable-libfaad --enable-libfaac --enable-xvid --enable-x264
  libavutil version: 49.3.0
  libavcodec version: 51.38.0
  libavformat version: 51.10.0
  built on Feb 17 2008 14:19:46, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Input #0, mpeg, from 'test.mpg':
  Duration: 00:04:58.8, start: 0.500000, bitrate: 5501 kb/s
  Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x576, 9000 kb/s, 25.00 fps(r)
  Stream #0.1[0x80]: Audio: ac3, 4800
```

which seems correct to me also.

Now, when I run dvdauthor the output is as follows:

```
WARN: unknown mpeg2 aspect ratio 4
WARN: unknown mpeg2 aspect ratio 4
WARN: unknown mpeg2 aspect ratio 4
WARN: unknown mpeg2 aspect ratio 4
WARN: unknown mpeg2 aspect ratio 4

INFO: Video pts = 0.500 .. 299.620
INFO: Audio[0] pts = 0.500 .. 299.572
STAT: VOBU 498 at 195MB, 1 PGCS
WARN: aspect ratio was not autodetected
INFO: Generating VTS with the following video attributes:
INFO: MPEG version: mpeg2
INFO: TV standard: pal
INFO: Aspect ratio: 4:3
INFO: Resolution: 720x576
INFO: Audio ch 0 format: ac3/6ch, 48khz drc

STAT: fixed 498 VOBUS                         
INFO: dvdauthor creating table of contents
INFO: Scanning test/VIDEO_TS/VTS_01_0.IFO

```

The resulting dvd is as described in my first post. Stretched vertically.

So any ideas how I can make dvdauthor handle it correctly?

Thanks in advance.
Phil

---

### Post by pssturges on 2010-10-19
Bump!

---

