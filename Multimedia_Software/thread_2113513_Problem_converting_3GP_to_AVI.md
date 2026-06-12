---
title: "Problem converting 3GP to AVI"
date: 2013-02-07
forum: Multimedia Software
---

### Post by DENNISBA31 on 2013-02-07
Hi I'm new in Ubuntu, and need to convert a 3GP video to AVI, and do not know how. IF ANYONE CAN HELP ME, I HAVE INSTALLED THE MOBILE MEDIA CONVERTER IN UBUNTU 12.04. And when I try to convert a video throws me the following error:

Command executed >>:
ffmpeg-i "/ home/dennis/Escritorio/TEMPORALES/camera/MiVideo_14.3gp"-f avi-vcodec msmpeg4v2-r 25-b-2000K ACODEC libmp3lame-ac 2-ar 44100-ab 128k "/ home / dennis / Desktop / TEMPORALES/camera/MiVideo_14.avi "

>> Result:
ffmpeg version 0.8.5-4:0.8.5-0 ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
** Built on January 24 2013 18:03:14 with gcc 4.6.3
THIS PROGRAM IS DEPRECATED *** ***
This program is provided for compatibility only and will be removed in a future release. Please use avconv place.
[Mov, mp4, m4a, 3gp, 3g2, MJ2 @ 0x9a65220] max_analyze_duration reached
Input # 0, mov, mp4, m4a, 3gp, 3g2, MJ2, from '/ home/dennis/Escritorio/TEMPORALES/camera/MiVideo_14.3gp':
** metadata:
**** major_brand: 3gp5
**** minor_version: 0
**** compatible_brands: 3gp5isom
**** creation_time: 02/01/2013 22:24:12
** Duration: 00:00:23.76, start: 0.000000, bitrate: 77 kb / s
**** Stream # 0.0 (eng): Video: MPEG4 (Simple Profile), yuv420p, 176x144 [PAR 1:01 DAR 11:09] 66 kb / s, 7.03 fps, 30 tbr, 1k tbn, 30 tbc
**** metadata:
****** creation_time: 02/01/2013 22:24:12
**** Stream # 0.1 (eng): Audio: SEVC / 0x63766573, 8000 Hz, 2 channels, 9 kb / s
**** metadata:
****** creation_time: 02/01/2013 22:24:12
[Buffer @ 0x9a685a0] w: 176 h: 144 pixfmt: yuv420p
Incompatible sample format '(null)' to 'libmp3lame' codec, self-selection "s16" format
Output # 0, avi, to '/ home/dennis/Escritorio/TEMPORALES/camera/MiVideo_14.avi':
**** Stream # 0.0 (eng): Video: msmpeg4v2, yuv420p, 176x144 [PAR 1:01 DAR 11:09], q = 2-31, 2000 kb / s, 90k tbn, 25 tbc
**** metadata:
****** creation_time: 02/01/2013 22:24:12
**** Stream # 0.1 (eng): Audio: libmp3lame, 44100 Hz, 2 channels, s16, 128 kb / s
**** metadata:
****** creation_time: 02/01/2013 22:24:12
Stream mapping:
** Stream # 0.0 -> # 0.0
** Stream # 0.1 -> # 0.1
Decoder (codec id 0) not found for input stream # 0.1

Sorry for my bad English, and thank you!

---

### Post by ron999 on 2013-02-07
> **DENNISBA31 said:**
> 
**** Stream # 0.1 (eng): Audio: SEVC / 0x63766573, 8000 Hz, 2 channels, 9 kb / s
...
Decoder (codec id 0) not found for input stream # 0.1
Hi
The soundtrack of your 3gp file uses:-
"Audio: SEVC / 0x63766573, 8000 Hz, 2 channels"

It looks like your version of "MOBILE MEDIA CONVERTER" can not read SEVC.

If you upload a sample file somewhere, maybe somebody will suggest a different converter to use.

---

### Post by FakeOutdoorsman on 2013-02-07
FFmpeg has an [EVRC decoder](http://git.videolan.org/?p=ffmpeg.git;a=commit;h=098d3891be08ca119e20ad7989668ddef83b31ea) as of 2013-01-21.

You will have to use a newer version. Either [compile ffmpeg](http://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide) or use a [static build](https://ffmpeg.org/download.html#LinuxBuilds).

---

