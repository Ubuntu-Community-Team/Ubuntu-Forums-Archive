---
title: "Command to find the resolution of a video file"
date: 2010-06-13
forum: Multimedia Software
---

### Post by jae1227 on 2010-06-13
I need to know a command that is able find the hight and width of a video. I know in VLC you can go into the Codec details but I need something in the command line because I have hundreds of files that I need to organize. I could not find any VLC command that does what I want to do. Any help is appreciated.

---

### Post by nothingspecial on 2010-06-13
[[COLOR="Magenta"]This[/COLOR]]("http://wesleybailey.com/articles/ffmpeg-tutorial-batch-processing-video-information") ought to help

---

### Post by FakeOutdoorsman on 2010-06-15
I didn't read the article linked above, but I use FFmpeg:
```
ffmpeg -i macro.mp4
```
Outputs a bunch of info including:
```
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'macro.mp4':
  Duration: 00:00:59.37, start: 0.000000, bitrate: 313 kb/s
    Stream #0.0(und): Video: h264, yuv420p, **640x480**, 29.97 tbr, 59.94 tbn, 119.88 tbc
    Stream #0.1(und): Audio: aac, 48000 Hz, stereo, s16
```
Another useful tool is [mediainfo](http://mediainfo.sourceforge.net/en/Download).

---

