---
title: "Making video file suitable for a Creative Zen"
date: 2007-04-11
forum: Multimedia &amp; Video
---

### Post by toasterofirony on 2007-04-11
I've been playing around making some of my video files into a suitable format/ resolution for playing on my Creative Zen and have hit something of a brickwall. I've been able to bend Avidemux to my will for anything .avi, but I have some .wmv files and a few .flv files that I would like to play on my Zen.

My problem is that I cannot figure out what arguments to make an mpeg4 file suitable. My current string is:

```
ffmpeg -i videofile.wmv -ab 56 -ar 22050 -b 500 -s 320x240 videofile.mpg
```

But when I try to play it on my Zen, I get an error message back that tells me it can't play the video at this bit rate. Rather than stumble around guessing, does anyone know what the correct bitrate is to end my woes?

---

### Post by quincy_the_penguin on 2007-04-29
I'm having this problem too...

---

