---
title: "How to print filename in video with Mencoder"
date: 2015-08-29
forum: Multimedia Software
---

### Post by danielbcjr on 2015-08-29
Hi, I´m using mencoder to convert a lot of jpgs in video.
How can I print the jpg filename in the video, like a OSD.

Can please anyone help me? =/

---

### Post by PaulW2U on 2015-08-30
*Thread moved to **Multimedia Software**.*

---

### Post by FakeOutdoorsman on 2015-08-31
Using ffmpeg:
```
 ffmpeg -i input.mkv -c:v mjpeg -q:v 2 -vf "drawtext=text='input.mkv':box=1:boxborderw=5:x=(w-tw)/2:y=h-th-th" output_%03d.jpg
```

[list]
[*]Change quality with -q:v. 2-6 is a good range to try. A lower value is a better quality.
[*]You should [download](http://johnvansickle.com/ffmpeg/) or [compile](http://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu) if you're not using 15.04 or newer (and even that may not support boxborderw). 14.04 users can use a [PPA](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media).
[*]See [drawtext](http://ffmpeg.org/ffmpeg-filters.html#drawtext) docs for more info.

[/list][ATTACH=CONFIG]264139[/ATTACH]

---

