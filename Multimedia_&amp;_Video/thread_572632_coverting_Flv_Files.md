---
title: "coverting Flv Files"
date: 2007-10-10
forum: Multimedia &amp; Video
---

### Post by markk1994 on 2007-10-10
I downloaded some videos of youtube can someone please help me how to convert them to wmv or something

---

### Post by amoocool on 2007-10-12
ffmpeg -i   *filename*.flv  *filename*.avi
converts to avi 
 get ffmpeg first if its not there

---

### Post by darkazurka on 2007-10-14
(I'm using Ubuntu feisty 7.04)

I tried these things for my VP6 encoded flv file:
1. ```
ffmpeg -i yo.flv yoyo.avi
```
2. ```
ffmpeg -i yo.flv yoyo.flv
```

These both gave lots of lines with: ```
[flv @ 0xb7f5e2d0]Unsupported video codec
``` (4). Didn't work, and gave a blank .avi file.

The package of ffmpeg I have installed is : 3:0.cvs20060823-3.1ubuntu4 (feisty)

I've read of someone having the same issue, and that it wasn't supported in maybe this version I have, but since there are not any new packages of ffmpeg I can't do anything. Has anyone had the same version as me, and it worked out fine?

---

### Post by eye208 on 2007-10-15
ffmpeg is a popular tool, but it cannot do everything. If ffmpeg fails, the next thing to check out is mencoder.

The rule of thumb is: If mplayer can play it, mencoder can transcode it. So far, mplayer has been able to play all my FLVs well. So try this:

mencoder input.flv -ovc x264 -oac mp3lame -o output.avi

This will give you an AVI file with H.264 video and MP3 audio. If that's not what you want, there are plenty of other codecs available in mencoder.

---

### Post by stooshbunutu on 2008-03-11
Use a GUI for ffmpeg called winff

[http://www.biggmatt.com/winff](http://www.biggmatt.com/winff)

---

