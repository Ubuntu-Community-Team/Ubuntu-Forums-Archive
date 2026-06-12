---
title: "Convert FLV to 3gp"
date: 2012-10-11
forum: Multimedia Software
---

### Post by spikoley on 2012-10-11
I am trying to convert a flash file to 3gp to play on my phone.  I have ffmpeg installed, but cannot figure out what options I need.

The example file below was recorded from my phone and plays.
```
ffmpeg -i example.3gp 
ffmpeg version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:37:58 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'example.3gp':
  Metadata:
    major_brand     : 3gp4
    minor_version   : 768
    compatible_brands: 3gp4mp413gp6
    creation_time   : 2012-05-19 05:53:30
    copyright       : 
    copyright-eng   : 
  Duration: 00:00:18.43, start: 0.000000, bitrate: 119 kb/s
    Stream #0.0(eng): Video: mpeg4 (Simple Profile), yuv420p, 352x288 [PAR 1:1 DAR 11:9], 104 kb/s, 14.64 fps, 1k tbr, 1k tbn, 1k tbc
    Metadata:
      creation_time   : 2012-05-19 05:53:30
    Stream #0.1(eng): Audio: amrnb, 8000 Hz, 1 channels, flt, 12 kb/s
    Metadata:
      creation_time   : 2012-05-19 05:53:30
At least one output file must be specified
```

---

### Post by ron999 on 2012-10-11
> **spikoley said:**
> Stream #0.1(eng): Audio: amrnb, 8000 Hz, 1 channels, flt, 12 kb/s
Hi
Your example.3gp file uses **amrnb** audio.
I don't think there's a **amrnb** encoder codec available for the 12.04 version of FFmpeg.
Have you any more examples of files that play OK on the phone?
Or find specifications of the phone.

---

### Post by coldraven on 2012-10-11
Try this
```
ffmpeg -i InputVid.flv -s qcif -vcodec h263 -r 10 -b 180 -sameq -ab 64 -acodec aac -ac 1 -ar 22050 OutputVid.3gp
```

I found this here: [http://www.commandlinefu.com/commands/view/1594/convert-.flv-to-.3gp](http://www.commandlinefu.com/commands/view/1594/convert-.flv-to-.3gp)

---

### Post by FakeOutdoorsman on 2012-10-11
> **coldraven said:**
> Try this
```
ffmpeg -i InputVid.flv -s qcif -vcodec h263 -r 10 -b 180 -sameq -ab 64 -acodec aac -ac 1 -ar 22050 OutputVid.3gp
```

I found this here: [http://www.commandlinefu.com/commands/view/1594/convert-.flv-to-.3gp](http://www.commandlinefu.com/commands/view/1594/convert-.flv-to-.3gp)

Do not use -sameq: [sameq does not mean "same quality"](http://superuser.com/a/478550/110524). Also, this option was removed from upstream(s) a few days ago.

---

### Post by spikoley on 2012-10-11
Thanks for all the replies. I am still receiving errors.

> **FakeOutdoorsman said:**
> Do not use -sameq: [sameq does not mean "same quality"](http://superuser.com/a/478550/110524). Also, this option was removed from upstream(s) a few days ago.

```
ffmpeg -i Test.flv -s qcif -vcodec h263 -r 10 -b 180 -sameq -ab 64 -acodec aac -ac 1 -ar 22050 Test.3gp
```
I ran that command and got this error:

```
ffmpeg -i Test.flv -s qcif -vcodec h263 -r 10 -b 180 -sameq -ab 64 -acodec aac -ac 1 -ar 22050 Test.3gp
ffmpeg version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:37:58 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[flv @ 0x949a240] Estimating duration from bitrate, this may be inaccurate

Seems stream 0 codec frame rate differs from container frame rate: 59.94 (60000/1001) -> 30.00 (30/1)
Input #0, flv, from 'Test.flv':
  Metadata:
    audiosize       : 3816817
    canSeekToEnd    : true
    datasize        : 34533160
    hasAudio        : true
    hasCuePoints    : false
    hasKeyframes    : true
    hasMetadata     : true
    hasVideo        : true
    lasttimestamp   : 470
    metadatacreator : flvtool++ (Facebook, Motion project, dweatherford)
    totalframes     : 14078
    videosize       : 30158630
  Duration: 00:07:49.63, start: 0.000000, bitrate: 592 kb/s
    Stream #0.0: Video: h264 (High), yuv420p, 422x238 [PAR 1:1 DAR 211:119], 526 kb/s, 30 tbr, 1k tbn, 59.94 tbc
    Stream #0.1: Audio: aac, 48000 Hz, stereo, s16, 66 kb/s
[buffer @ 0x949e2c0] w:422 h:238 pixfmt:yuv420p
[scale @ 0x949ebe0] w:422 h:238 fmt:yuv420p -> w:176 h:144 fmt:yuv420p flags:0x4
**[COLOR="Red"][h263 @ 0x94af9e0] Invalid pixel aspect ratio 1899/1309, limit is 255/255[/COLOR]**
Output #0, 3gp, to 'Test.3gp':
    Stream #0.0: Video: h263, yuv420p, 176x144 [PAR 1899:1309 DAR 211:119], q=2-31, 0 kb/s, 90k tbn, 10 tbc
    Stream #0.1: Audio: libvo_aacenc, 22050 Hz, 1 channels, s16, 200 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Error while opening encoder for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height

```

---

### Post by spikoley on 2012-10-11
I got the video looking decent with the command below, but I have no sound.  Any ideas?

```
ffmpeg -i Test.flv -s qcif -vcodec h263 -r 10 -b 180 -sameq -ab 64 -acodec aac -ac 1 -ar 8000 -aspect 4:3 Test.3gpffmpeg version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:37:58 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[flv @ 0x857c240] Estimating duration from bitrate, this may be inaccurate

Seems stream 0 codec frame rate differs from container frame rate: 59.94 (60000/1001) -> 30.00 (30/1)
Input #0, flv, from 'Test.flv':
  Metadata:
    audiosize       : 3816817
    canSeekToEnd    : true
    datasize        : 34533160
    hasAudio        : true
    hasCuePoints    : false
    hasKeyframes    : true
    hasMetadata     : true
    hasVideo        : true
    lasttimestamp   : 470
    metadatacreator : flvtool++ (Facebook, Motion project, dweatherford)
    totalframes     : 14078
    videosize       : 30158630
  Duration: 00:07:49.63, start: 0.000000, bitrate: 592 kb/s
    Stream #0.0: Video: h264 (High), yuv420p, 422x238 [PAR 1:1 DAR 211:119], 526 kb/s, 30 tbr, 1k tbn, 59.94 tbc
    Stream #0.1: Audio: aac, 48000 Hz, stereo, s16, 66 kb/s
[buffer @ 0x85802c0] w:422 h:238 pixfmt:yuv420p
[scale @ 0x8580be0] w:422 h:238 fmt:yuv420p -> w:176 h:144 fmt:yuv420p flags:0x4
[B][COLOR="Sienna"]The bitrate parameter is set too low.It takes bits/s as argument, not kbits/s[/COLOR]
[COLOR="Red"]encoder 'aac' is experimental and might produce bad results.
Add '-strict experimental' if you want to use it.
Or use the non experimental encoder 'libvo_aacenc'.[/COLOR][/B]

```

---

### Post by spikoley on 2012-10-11
I got it working!

```
ffmpeg -i Test.flv -s qcif -vcodec h263 -r 10 -b 180 -sameq -ab 64 -acodec libvo_aacenc -ac 1 -ar 8000 -aspect 4:3 -strict experimental Test.3gp
```

---

### Post by FakeOutdoorsman on 2012-10-11
You should add *k* to *-b 180* and *-ab 64*, as in *-b 180k* and *-ab 64k* since these options take a value in bits, not kilobits. Remove *-sameq*.

---

