---
title: "winff/ffmpeg encoding dvds with bitrate that is too low"
date: 2012-07-23
forum: Multimedia Software
---

### Post by someitalian123 on 2012-07-23
I'm using winff to convert an av as a dvd I set the bitrate to 4851k but the resulting file has a bitrate that is less then half of that. The present I'm using is this.

```
-f dvd -target ntsc-dvd -r 23.976 -vf scale=720:480 -aspect 16:9 -b 4851k -g 12 -mbd rd -trellis 2 -flags +mv0 -cmp 0 -subcmp 2
```

and this is the encoding log

```

ffmpeg version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:37:58 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[mpeg4 @ 0x932b820] Invalid and inefficient vfw-avi packed B frames detected
[matroska,webm @ 0x9328260] Estimating duration from bitrate, this may be inaccurate
Input #0, matroska,webm, from '/home/anthony/Desktop/[Oyasumi]_Welcome_to_the_NHK!/[Oyasumi]_Welcome_to_the_NHK!_01_[B17D228B].mkv':
  Duration: 00:24:10.89, start: 0.000000, bitrate: N/A
    Chapter #0.0: start 0.000000, end 99.933000
    Metadata:
      title           : Opening
    Chapter #0.1: start 99.933000, end 1329.953000
    Metadata:
      title           : Welcome to the NHK 01: Welcome to the Project
    Chapter #0.2: start 1329.953000, end 1419.876000
    Metadata:
      title           : Ending
    Chapter #0.3: start 1419.876000, end 1450.890000
    Metadata:
      title           : Preview
    Stream #0.0: Video: mpeg4 (Advanced Simple Profile), yuv420p, 704x400 [PAR 1:1 DAR 44:25], 23.98 fps, 23.98 tbr, 1k tbn, 23.98 tbc (default)
    Metadata:
      title           : [oyasumi] Welcome to the NHK - 01 (XviD)
    Stream #0.1(jpn): Audio: vorbis, 48000 Hz, stereo, s16 (default)
    Metadata:
      title           : Stereo Vorbis
[buffer @ 0x93e7b00] w:704 h:400 pixfmt:yuv420p
[scale @ 0x936a340] w:704 h:400 fmt:yuv420p -> w:720 h:480 fmt:yuv420p flags:0x4
[scale @ 0x93a9d20] w:720 h:480 fmt:yuv420p -> w:720 h:480 fmt:yuv420p flags:0x4
Output #0, dvd, to '/dev/null':
  Metadata:
    encoder         : Lavf53.21.0
    Chapter #0.0: start 0.000000, end 99.933000
    Metadata:
      title           : Opening
    Chapter #0.1: start 99.933000, end 1329.953000
    Metadata:
      title           : Welcome to the NHK 01: Welcome to the Project
    Chapter #0.2: start 1329.953000, end 1419.876000
    Metadata:
      title           : Ending
    Chapter #0.3: start 1419.876000, end 1450.890000
    Metadata:
      title           : Preview
    Stream #0.0: Video: mpeg2video (hq), yuv420p, 720x480 [PAR 32:27 DAR 16:9], q=2-31, pass 1, 4851 kb/s, 90k tbn, 23.98 tbc (default)
    Metadata:
      title           : [oyasumi] Welcome to the NHK - 01 (XviD)
Stream mapping:
  Stream #0.0 -> #0.0
Press ctrl-c to stop encoding
[mpeg4 @ 0x9330460] Invalid and inefficient vfw-avi packed B frames detected
[mpeg2video @ 0x93699e0] rc buffer underflow
frame=34284 fps= 46 q=2.4 Lsize=       0kB time=1429.89 bitrate=   0.0kbits/s    
video:327009kB audio:0kB global headers:0kB muxing overhead -100.000000%
ffmpeg version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:37:58 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[mpeg4 @ 0x85f7820] Invalid and inefficient vfw-avi packed B frames detected
[matroska,webm @ 0x85f4260] Estimating duration from bitrate, this may be inaccurate
Input #0, matroska,webm, from '/home/anthony/Desktop/[Oyasumi]_Welcome_to_the_NHK!/[Oyasumi]_Welcome_to_the_NHK!_01_[B17D228B].mkv':
  Duration: 00:24:10.89, start: 0.000000, bitrate: N/A
    Chapter #0.0: start 0.000000, end 99.933000
    Metadata:
      title           : Opening
    Chapter #0.1: start 99.933000, end 1329.953000
    Metadata:
      title           : Welcome to the NHK 01: Welcome to the Project
    Chapter #0.2: start 1329.953000, end 1419.876000
    Metadata:
      title           : Ending
    Chapter #0.3: start 1419.876000, end 1450.890000
    Metadata:
      title           : Preview
    Stream #0.0: Video: mpeg4 (Advanced Simple Profile), yuv420p, 704x400 [PAR 1:1 DAR 44:25], 23.98 fps, 23.98 tbr, 1k tbn, 23.98 tbc (default)
    Metadata:
      title           : [oyasumi] Welcome to the NHK - 01 (XviD)
    Stream #0.1(jpn): Audio: vorbis, 48000 Hz, stereo, s16 (default)
    Metadata:
      title           : Stereo Vorbis
[buffer @ 0x8636860] w:704 h:400 pixfmt:yuv420p
[scale @ 0x86f1660] w:704 h:400 fmt:yuv420p -> w:720 h:480 fmt:yuv420p flags:0x4
[scale @ 0x868dbe0] w:720 h:480 fmt:yuv420p -> w:720 h:480 fmt:yuv420p flags:0x4
Incompatible sample format 's16' for codec 'ac3', auto-selecting format 'flt'
[mpeg2video @ 0x86359e0] [lavc rc] Using all of requested bitrate is not necessary for this video with these parameters.
Output #0, dvd, to '/home/anthony/Desktop/[Oyasumi]_Welcome_to_the_NHK!_01_[B17D228B].mpg':
  Metadata:
    encoder         : Lavf53.21.0
    Chapter #0.0: start 0.000000, end 99.933000
    Metadata:
      title           : Opening
    Chapter #0.1: start 99.933000, end 1329.953000
    Metadata:
      title           : Welcome to the NHK 01: Welcome to the Project
    Chapter #0.2: start 1329.953000, end 1419.876000
    Metadata:
      title           : Ending
    Chapter #0.3: start 1419.876000, end 1450.890000
    Metadata:
      title           : Preview
    Stream #0.0: Video: mpeg2video (hq), yuv420p, 720x480 [PAR 32:27 DAR 16:9], q=2-31, pass 2, 4851 kb/s, 90k tbn, 23.98 tbc (default)
    Metadata:
      title           : [oyasumi] Welcome to the NHK - 01 (XviD)
    Stream #0.1(jpn): Audio: ac3, 48000 Hz, stereo, flt, 192 kb/s (default)
    Metadata:
      title           : Stereo Vorbis
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press ctrl-c to stop encoding
Input stream #0.1 frame changed from rate:48000 fmt:s16 ch:2 to rate:48000 fmt:flt ch:2
[mpeg4 @ 0x8632f40] Invalid and inefficient vfw-avi packed B frames detected
frame=34284 fps= 41 q=2.4 Lsize=  375220kB time=1429.89 bitrate=2149.7kbits/s    
video:327902kB audio:34005kB global headers:0kB muxing overhead 3.678506%
Press Enter to Continue
```
[http://www.mediafire.com/?nia3l4r0c6u846m](http://www.mediafire.com/?nia3l4r0c6u846m)

---

