---
title: "Newb help getting video info with ffmpeg/mplayer"
date: 2010-02-19
forum: Multimedia Software
---

### Post by jakezz on 2010-02-19
Hi I am trying to get a listing of video information using ffmpeg or mplayer. I have found a way BUT it is only returning 1 piece of info..

Here is what I'm doing in PHP:

print exec("/usr/local/bin/mplayer -identify file.flv -ao null -vo null -frames 0 2>/dev/null | grep ^ID_");

But this will not provide an entire listing, it will only print out 1 thing such as:
ID_AUDIO_CODEC=mp3

I can specify what exactly I want to know something like:

print exec("/usr/local/bin/mplayer -identify file.flv -ao null -vo null -frames 0 2>/dev/null | grep ^ID_VIDEO_WIDTH");

but I want to just have all the info available at once instead of having to loop through like 20 times..

---

### Post by SuperSonic4 on 2010-02-19
```
ffmpeg -i *file*
```

For example
```
ffmpeg -i dwhelper/See\ me\ in\ Shadow
Seems stream 0 codec frame rate differs from container frame rate: 50.00 (50/1) -> 25.00 (25/1)
Input #0, flv, from 'dwhelper/See me in Shadow':
  Metadata:
    duration        : 225
    starttime       : 0
    totalduration   : 225
    width           : 480
    height          : 360
    videodatarate   : 469
    audiodatarate   : 101
    totaldatarate   : 577
    framerate       : 25
    bytelength      : 16252574
    canseekontime   : true
    sourcedata      : B5ADFF446HH
    purl            :
    pmsg            :
  Duration: 00:03:44.96, start: 0.000000, bitrate: 479 kb/s
    Stream #0.0: Video: h264, yuv420p, 480x360 [PAR 1:1 DAR 4:3], 479 kb/s, 50 fps, 25 tbr, 1k tbn, 50 tbc
    Stream #0.1: Audio: aac, 44100 Hz, stereo, s16
```

---

### Post by jakezz on 2010-02-19
> **SuperSonic4 said:**
> ```
ffmpeg -i *file*
```For example
```
ffmpeg -i dwhelper/See\ me\ in\ Shadow
Seems stream 0 codec frame rate differs from container frame rate: 50.00 (50/1) -> 25.00 (25/1)
Input #0, flv, from 'dwhelper/See me in Shadow':
  Metadata:
    duration        : 225
    starttime       : 0
    totalduration   : 225
    width           : 480
    height          : 360
    videodatarate   : 469
    audiodatarate   : 101
    totaldatarate   : 577
    framerate       : 25
    bytelength      : 16252574
    canseekontime   : true
    sourcedata      : B5ADFF446HH
    purl            :
    pmsg            :
  Duration: 00:03:44.96, start: 0.000000, bitrate: 479 kb/s
    Stream #0.0: Video: h264, yuv420p, 480x360 [PAR 1:1 DAR 4:3], 479 kb/s, 50 fps, 25 tbr, 1k tbn, 50 tbc
    Stream #0.1: Audio: aac, 44100 Hz, stereo, s16
```

<?php
print exec("/usr/local/bin/ffmpeg -i file.flv");
?>

Is this correct^? I have tried this and it prints nothing onto the page.. I'm trying to load all the video info into a variable or array to use in PHP.

This below will get me any 1 value that I specify, but do I really want to run a loop ~20 times to gather all the info?:

print exec("mplayer -identify file.flv -ao null -vo null -frames 0 2>/dev/null | grep ^ID_");

---

### Post by SuperSonic4 on 2010-02-19
I have no idea with scripts or php I'm afraid

---

