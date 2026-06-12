---
title: "adding a logo in a video with a software that works?"
date: 2014-01-21
forum: Multimedia Software
---

### Post by pozitronios on 2014-01-21
All I want to do is add a logo in the top right corner in a couple of videos on ubuntu 12

I have been trying over a week with a bunch of software, one doesn't render (pitivi) the other crashes kdenlive, other just don't do what I want.

I have grown desperate, do you know a simple software that can do that?

Thank you

---

### Post by TheFu on 2014-01-22
[http://www.linuxquestions.org/questions/linux-software-2/ffmpeg-how-to-add-watermark-to-a-video-via-shell-865102/](http://www.linuxquestions.org/questions/linux-software-2/ffmpeg-how-to-add-watermark-to-a-video-via-shell-865102/)
might work.

---

### Post by pozitronios on 2014-01-22
Using openshot, however the preview doesn't work as expected shows wrong aspect ratio than my project settings and have to export everytime I have to preview actual changes

---

### Post by FakeOutdoorsman on 2014-01-23
If you don't mind using a command-line tool you can use ffmpeg. Using the [overlay video filter](https://ffmpeg.org/ffmpeg-filters.html#overlay-1):

```
ffmpeg -i video.mp4 -i logo.png -filter_complex "[0:v][1:v]overlay=main_w-overlay_w-10:10[filtered]" -map "[filtered]" -map 0:a -codec:a copy output.mp4
```

[list]
[*]**[0:v]** refers to the video stream(s) of the first input (video.mp4).
[*]**[1:v]** refers to the video stream(s) of the second input (logo.png).
[*]**main_w** is the width of the "main" input (video.mp4).
[*]**overlay_w** is the width of the "overlay" input (logo.png).
[*]The audio from video.mp4 is [stream copied](https://ffmpeg.org/ffmpeg.html#Stream-copy) instead of re-encoded.
[/list]

This example will place the logo in the upper right: 10 pixels from the right side, and 10 pixels down from the top. See the [FFmpeg and x264 Encoding Guide](https://trac.ffmpeg.org/wiki/x264EncodingGuide) for getting a good quality output.

---

