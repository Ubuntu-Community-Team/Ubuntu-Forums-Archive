---
title: "Editing .ogm files"
date: 2008-11-21
forum: Multimedia Software
---

### Post by change_mode on 2008-11-21
I got some ogm files that include a video, two audio tracks and subtitles. I want to remove one of the audio tracks and the subtitles, but how?

I got avidemux which has been great so far for editing, but it doesn't even open .ogm files.

---

### Post by FakeOutdoorsman on 2008-11-21
This should be easy to do with ffmpeg, and you won't even need to encode anything because you can just copy the streams. First find out the codecs and other info about the file.  I don't have an OGM file, so I'll use a VOB as an example:
```
ffmpeg -i VTS_01_1.VOB
```
It outputs a bunch of stuff, but the "stream" info is the most important for now:
```
Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480 [PAR 32:27 DAR 16:9], 9800 kb/s, 59.94 tb(r)
Stream #0.1[0x80]: Audio: ac3, 48000 Hz, stereo, s16, 192 kb/s
Stream #0.2[0x81]: Audio: ac3, 48000 Hz, stereo, s16, 192 kb/s
Stream #0.3[0x2d]: Subtitle: dvdsub
```
If I just want the video (Stream #0.0) and one audio stream (Stream #0.2):
```
ffmpeg -i inputvideo.ogm -map 0:0 -map 0:2 -vcodec copy -acodec copy -f ogg output.ogm
```
This last command should be very quick because there is no transcoding.

---

