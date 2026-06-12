---
title: "ffmpeg doesn't recognize ac3 after fresh 12.04 install"
date: 2012-07-04
forum: Multimedia Software
---

### Post by Nutria on 2012-07-04
Hi,

Back in the 10.10 days, this worked to increase the volume of videos:

```
VID=foo.mkv
ffmpeg -i $VID -vcodec copy -vol 512 -c:a ac3 -b:a 192k -r:a 48k louder/$VID
```

Now it fails with:
```
ffmpeg -i foo.mkv -vcodec copy -vol 512 -c:a ac3 -b:a 192k -r:a 48k louder/foo.mkv
ffmpeg version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:52:09 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[matroska,webm @ 0x17aa9a0] Estimating duration from bitrate, this may be inaccurate

Seems stream 0 codec frame rate differs from container frame rate: 180000.00 (180000/1) -> 1000.00 (1000/1)
Input #0, matroska,webm, from 'foo.mkv':
  Duration: 00:49:20.09, start: 0.000000, bitrate: 224 kb/s
    Chapter #0.0: start 0.000000, end 420.186433
    Metadata:
      title           : Chapter 1
    Chapter #0.1: start 420.186433, end 840.105933
    Metadata:
[snip]
    Metadata:
      title           : Chapter 8
    Stream #0.0(eng): Video: h264 (High), yuv420p, 704x480 [PAR 10:11 DAR 4:3], 29.97 fps, 1k tbr, 1k tbn, 180k tbc (default)
    Stream #0.1(eng): Audio: ac3, 48000 Hz, stereo, s16, 224 kb/s (default)
[COLOR="Red"]Unrecognized option 'c:a'
Failed to set value 'ac3' for option 'c:a'[/COLOR]
```

Here are, I think, the relative packages installed on my machine:
```
$ apt-cache policy libavcodec53 ffmpeg
libavcodec53:
  Installed: 4:0.8.3-0ubuntu0.12.04.1
  Candidate: 4:0.8.3-0ubuntu0.12.04.1
  Version table:
 *** 4:0.8.3-0ubuntu0.12.04.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ precise-security/main amd64 Packages
        100 /var/lib/dpkg/status
     4:0.8.1-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
ffmpeg:
  Installed: 4:0.8.3-0ubuntu0.12.04.1
  Candidate: 4:0.8.3-0ubuntu0.12.04.1
  Version table:
 *** 4:0.8.3-0ubuntu0.12.04.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ precise-security/main amd64 Packages
        100 /var/lib/dpkg/status
     4:0.8.1-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages

```

---

### Post by ron999 on 2012-07-04
Hi
Your version of FFmpeg doesn't recognize options such as "-c:a".
So change
**-c:a ac3** into **-acodec ac3**
**-b:a 192k** into **-ab 192k**
**-r:a 48k** into **-ar 48k**

---

### Post by Nutria on 2012-07-04
> **ron999 said:**
> Hi
Your version of FFmpeg doesn't recognize options such as "-c:a".

Thanks. Why the change back to the way I seem to remember ffmpeg doing it back in the day?

> 
**-c:a ac3** into **-acodec ac3**
**-b:a 192k** into **-ab 192k**
**-r:a 48k** into **-ar 48k**

No joy in Mudville.  Also, they seem to have removed "-vol" support.

```
$ avconv -i foo.mkv \
       -vcodec copy \
       -vol 512 \
       -acodec ac3 -ab 224 -ar 48k loud.mkv
avconv version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:52:09 with gcc 4.6.3
[matroska,webm @ 0x1c7c7a0] Estimating duration from bitrate, this may be inaccurate
Input #0, matroska,webm, from 'foo.mkv':
  Duration: 01:53:43.08, start: 0.000000, bitrate: 224 kb/s
    Chapter #0.0: start 0.000000, end 199.966433
    Metadata:
      title           : Chapter 1
[snip]
    Chapter #0.9: start 6230.190633, end 6823.083000
    Metadata:
      title           : Chapter 10
    Stream #0.0(eng): Video: h264 (High), yuv420p, 720x480 [PAR 853:720 DAR 853:480], PAR 186:157 DAR 279:157, 29.97 fps, 1k tbr, 1k tbn, 180k tbc (default)
    Stream #0.1(eng): Audio: ac3, 48000 Hz, stereo, s16, 224 kb/s (default)
Incompatible sample format 's16' for codec 'ac3', auto-selecting format 'flt'
[ac3 @ 0x1c84800] invalid bit rate
Output #0, matroska, to 'loud.mkv':
    Chapter #0.0: start 0.000000, end 199.966433
    Metadata:
      title           : Chapter 1
[snip]
    Chapter #0.9: start 6230.190633, end 6823.083000
    Metadata:
      title           : Chapter 10
    Stream #0.0(eng): Video: [0][0][0][0] / 0x0000, yuv420p, 720x480 [PAR 186:157 DAR 279:157], q=2-31, 90k tbn, 1k tbc (default)
    Stream #0.1(eng): Audio: ac3, 48000 Hz, stereo, flt, 0 kb/s (default)
Stream mapping:
  Stream #0:0 -> #0:0 (copy)
  Stream #0:1 -> #0:1 (ac3 -> ac3)
Error while opening encoder for output stream #0:1 - maybe incorrect parameters such as bit_rate, rate, width or height
```

---

### Post by ron999 on 2012-07-04
> **Nutria said:**
> Thanks. Why the change back to the way I seem to remember ffmpeg doing it back in the day?
Beats me :p

> **Nutria said:**
> 
No joy in Mudville.

```
$ avconv -i foo.mkv \
       -vcodec copy \
       -vol 512 \
       -acodec ac3 -ab 224 -ar 48k loud.mkv

Error while opening encoder for output stream #0:1 
- maybe incorrect parameters such as [COLOR="Red"]bit_rate[/COLOR], rate, width or height
```

Bitrate needs to be 224[COLOR="Red"]k[/COLOR]
;)

---

### Post by Nutria on 2012-07-04
> **ron999 said:**
> Bitrate needs to be 224[COLOR="Red"]k[/COLOR]
;)

Bah.  The ffmpeg/libav teams need to go back to kindergarten and learn to play nice together.



```
$ avconv -i foo.mkv \
     -vcodec copy \
     -vol 512 \
     -acodec ac3 -ab 224k -ar 48k loud.mkv
avconv version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:52:09 with gcc 4.6.3
[matroska,webm @ 0x7d97a0] Estimating duration from bitrate, this may be inaccurate
Input #0, matroska,webm, from 'foo.mkv':
  Duration: 01:53:43.08, start: 0.000000, bitrate: 224 kb/s
[snip]
    Stream #0.0(eng): Video: h264 (High), yuv420p, 720x480 [PAR 853:720 DAR 853:480], PAR 186:157 DAR 279:157, 29.97 fps, 1k tbr, 1k tbn, 180k tbc (default)
    Stream #0.1(eng): Audio: ac3, 48000 Hz, stereo, s16, 224 kb/s (default)
Incompatible sample format 's16' for codec 'ac3', auto-selecting format 'flt'
Output #0, matroska, to 'loud.mkv':
  Metadata:
    encoder         : Lavf53.21.0
    Stream #0.0(eng): Video: H264 / 0x34363248, yuv420p, 720x480 [PAR 186:157 DAR 279:157], q=2-31, 1k tbn, 1k tbc (default)
    Stream #0.1(eng): Audio: ac3, 48000 Hz, stereo, flt, 224 kb/s (default)
Stream mapping:
  Stream #0:0 -> #0:0 (copy)
  Stream #0:1 -> #0:1 (ac3 -> ac3)
Press ctrl-c to stop encoding
Input stream #0:1 frame changed from rate:48000 fmt:s16 ch:2 to rate:48000 fmt:flt ch:2
[COLOR="Red"][matroska @ 0x80d820] Application provided invalid, non monotonically increasing dts to muxer in stream 0: -67 >= -67
av_interleaved_write_frame(): Invalid argument[/COLOR]

```

Others have noticed it in stock ffmpeg:
[http://ffmpeg.org/pipermail/ffmpeg-user/2011-November/003389.html](http://ffmpeg.org/pipermail/ffmpeg-user/2011-November/003389.html)

---

### Post by ron999 on 2012-07-04
> **Nutria said:**
> 
Others have noticed it in **stock** ffmpeg:


Hi
Seems like a good enough reason to compile FFmpeg from git ---> [https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide]("https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide")
;)

---

