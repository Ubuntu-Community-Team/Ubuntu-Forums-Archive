---
title: "Convert to 3gp with ffmpeg"
date: 2012-11-10
forum: Multimedia Software
---

### Post by isa.dsouza on 2012-11-10
I tried running this command to convert to 3gp with no luck.

ffmpeg -i *filename.flv* -s qcif -vcodec h264 -b 200k -acodec libfaac -ab 64k -y *filename*.3gp

ffmpeg version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:37:58 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[flv @ 0x8f74240] Estimating duration from bitrate, this may be inaccurate
Input #0, flv, from '*filename*.*flv*':
  Metadata:
    starttime       : 0
    totalduration   : 170
    totaldatarate   : 335
    bytelength      : 7146005
    canseekontime   : true
    sourcedata      : B4A7D6203HH1300837429600021
    purl            : 
    pmsg            : 
  Duration: 00:02:50.24, start: 0.000000, bitrate: 335 kb/s
    Stream #0.0: Video: h264 (Main), yuv420p, 320x240 [PAR 1:1 DAR 4:3], 281 kb/s, 25 tbr, 1k tbn, 50 tbc
    Stream #0.1: Audio: aac, 44100 Hz, mono, s16, 53 kb/s
Unknown encoder 'h264'

ffmpeg -i *filename.flv* -s qcif -vcodec h264 -b 200k -acodec libvo_aacenc -ab 64k -y *filename*.3gp

ffmpeg version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:37:58 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[flv @ 0x9218240] Estimating duration from bitrate, this may be inaccurate
Input #0, flv, from '*filename*.*flv*':
  Metadata:
    starttime       : 0
    totalduration   : 170
    totaldatarate   : 335
    bytelength      : 7146005
    canseekontime   : true
    sourcedata      : B4A7D6203HH1300837429600021
    purl            : 
    pmsg            : 
  Duration: 00:02:50.24, start: 0.000000, bitrate: 335 kb/s
    Stream #0.0: Video: h264 (Main), yuv420p, 320x240 [PAR 1:1 DAR 4:3], 281 kb/s, 25 tbr, 1k tbn, 50 tbc
    Stream #0.1: Audio: aac, 44100 Hz, mono, s16, 53 kb/s
Unknown encoder 'h264'

---

### Post by nothingspecial on 2012-11-10
Question moved to it's own thread.

---

### Post by isa.dsouza on 2012-11-10
Answer in this thread [http://ubuntuforums.org/showthread.php?t=1254647](http://ubuntuforums.org/showthread.php?t=1254647)

---

### Post by evilsoup on 2012-11-10
'h264' isn't a valid encoder in ffmpeg, you'd need to use 'libx264' instead. [here](https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide) is a guide for encoding with libx264. Used correctly, this will get you better quality/size than using mpeg4.

---

### Post by isa.dsouza on 2012-11-11
I guessed as much about the h264 bit. I will give the guide a shot. It is very complicated though. :)

---

### Post by FakeOutdoorsman on 2012-11-11
> **isa.dsouza said:**
> I guessed as much about the h264 bit. I will give the guide a shot. It is very complicated though. :)

If there are some particular confusing sections, or if you have any suggestions to make it more user friendly, then please let me know.

---

