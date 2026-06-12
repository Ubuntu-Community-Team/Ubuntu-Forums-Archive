---
title: "trouble with ffmpeg"
date: 2012-09-30
forum: Multimedia Software
---

### Post by sn0m on 2012-09-30
Hi guys
Sth's gonna funny with my last update and ffmpeg doesn't do the job any more.
I'm trying to convert an avi video to mp4 format and this is what I get:
ffmpeg -i day_trip.avi -f mp4 -vcodec libxvid -s 640x360 -b 768kb -r 25 -aspect 16:9 -acodec libfaac0 -ab 96kb -ar 44100 -ac 2 day_trip.mp4
ffmpeg version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:52:09 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
Input #0, avi, from 'day_trip.avi':
  Duration: 01:48:26.92, start: 0.000000, bitrate: 1957 kb/s
    Stream #0.0: Video: mpeg4 (Simple Profile), yuv420p, 720x384 [PAR 1:1 DAR 15:8], 25 tbr, 25 tbn, 25 tbc
    Stream #0.1: Audio: ac3, 48000 Hz, 5.1, s16, 384 kb/s
Unknown encoder 'libfaac0'


I checked and i do have libfaac0 in synaptic?
Any help is appreciated
Regards
Sokol

---

### Post by Merrattic on 2012-09-30
First off, try using avconv instead of ffmpeg (syntax is much the same)

Alternatively, compile ffmpeg from source using FakeOutdoorsman's excellent guide (See Tutorials & Tips) and you will be back where you started but in much better shape!

---

### Post by ron999 on 2012-09-30
> **sn0m said:**
> 
Unknown encoder 'libfaac0'

Hi
With FFmpeg from the Ubuntu-12.04 repository....
Install the extra codecs:-
```
sudo apt-get install libavcodec-extra-53
```
Then use a command like this:-
```
ffmpeg -i day_trip.avi -vcodec libxvid -s 640x360 -b 768k -r 25 -aspect 16:9 -acodec libvo_aacenc -ab 96k -ar 44100 -ac 2 day_trip.mp4
```

Explanation....
Your version of FFmpeg has been compiled with a different aac encoder.
Uses libvo_aacenc instead of libfaac.
With command **ffmpeg -codecs** you see that libfaac isn't on the list.

---

### Post by odjiri on 2013-05-10
> **ron999 said:**
> Hi
With FFmpeg from the Ubuntu-12.04 repository....
[B]Install the extra codecs:-
```
sudo apt-get install libavcodec-extra-53
```[/B]
Then use a command like this:-
```
ffmpeg -i day_trip.avi -vcodec libxvid -s 640x360 -b 768k -r 25 -aspect 16:9 -acodec libvo_aacenc -ab 96k -ar 44100 -ac 2 day_trip.mp4
```

Explanation....
Your version of FFmpeg has been compiled with a different aac encoder.
Uses libvo_aacenc instead of libfaac.
With command **ffmpeg -codecs** you see that libfaac isn't on the list.

Thank you, it worked for me, too!
I had analogeous problem ( *Unknown encoder 'libvo_aacenc'* ) while trying to convert AVI to 3GP using WinFF.

---

