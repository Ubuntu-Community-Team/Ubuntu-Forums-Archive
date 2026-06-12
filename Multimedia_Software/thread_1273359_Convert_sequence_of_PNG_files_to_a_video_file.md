---
title: "Convert sequence of PNG files to a video file"
date: 2009-09-23
forum: Multimedia Software
---

### Post by dsavi on 2009-09-23
I have a pretty big sequence (649) of PNG files that I want to convert to one video file. The format of the video file doesn't really matter. I understand the tool to use is ffmpeg, but I can't figure it out, there are far too many options to understand. The files are named 0001.png to 0649.png.
Can someone help?

---

### Post by FakeOutdoorsman on 2009-09-23
You're right that FFmpeg is the tool to use for this.  Here's an example that should convert your images to H.264 video in a MP4 container.
```
ffmpeg -i %04d.png -vcodec libx264 -vpre hq -crf 22 -threads 0 output.mp4
```
More info:
[list][*] [FFmpeg FAQ: How do I encode single pictures into movies?](http://ffmpeg.org/faq.html#SEC14)
[*] [FFmpeg x264 encoding guide](http://rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/)[/list]

---

