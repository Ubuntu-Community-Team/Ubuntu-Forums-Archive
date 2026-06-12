---
title: "DevedeNG now has HEVC support."
date: 2019-11-02
forum: Multimedia Software
---

### Post by jasper99 on 2019-11-02
DevedeNG now has HEVC support: [URL="https://gitlab.com/rastersoft/devedeng/tree/h265_support"]https://gitlab.com/rastersoft/devedeng/tree/h265_support

I'm happy with it and it works great, only min is that it convert to a "low" 3,8 GB size instead of the 4,38 GB DVD size.
And it does not hold the original file names.

[IMG]https://i.postimg.cc/Jhcy91jt/Devede-NG-H265-HEVC.png[/IMG][/URL]

---

### Post by uRock on 2019-11-02
I'm looking forward to the day they start supporting 1080p and 4k.

---

### Post by jasper99 on 2019-11-02
1080p is already supported in H264 and HEVC.

---

### Post by uRock on 2019-11-02
I've tried those options. They just create mpg files. Here's the 1080p quality made from an 11GB video file. The only option that creates a usable image is the Video DVD option, which only offers 720p.

---

### Post by jasper99 on 2019-11-03
Is youtube-dl installed? required for HEVC converting.

---

### Post by mc4man on 2019-11-03
> **jasper99 said:**
> Is youtube-dl installed? required for HEVC converting.
That has nothing to do with it.. Can use that option  in deveded here with or without youtube-dl, it also not listed in "Programs needed by devede" tab

Anyway the hevc encoding seems to have limited use, not sure what it's use case is??

The encoding is using ffmpeg in bitrate mode, by default it uses 2000 kb/s, also setting a min and max rate. 
It converts audio to mp3.
Moving the "Adjust disc usage" slider will either raise or lower the set bitrate, quite possible to actually end up with a larger file size than orig. (wasted bitrate..

The window make one choose pal or ntsc, really irrelevant as no fps conversion will be done anyway.

generically a far better job can be done using ffmpeg directly using crf and a preset, only value I see here is it does  bitrate  math calculation for you in rare case that bitrate mode is wanted over crf..

---

