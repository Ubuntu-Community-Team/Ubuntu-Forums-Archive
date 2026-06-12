---
title: "Help with video codec in ffmpeg"
date: 2011-08-31
forum: Multimedia Software
---

### Post by distended on 2011-08-31
Hi all,

I'm trying to make a video from a series of images.  Using
[FONT=monospace]
[/FONT]ffmpeg -f image2 -i image%d.jpg video.mpg

works fine, except for the fact that the resulting video is about 3 seconds long, when ideally it would be about 20 seconds long.

When I try to limit the framerate with -r, I get  a red warning that "mpeg1/2 does not support 5/1 fps"

I have very little idea what I'm doing.  Is there some alternative way to limit the framerate, or a codec that supports very low framerates?  Thanks for any help.

---

