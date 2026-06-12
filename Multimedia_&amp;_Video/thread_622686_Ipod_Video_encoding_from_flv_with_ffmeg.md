---
title: "Ipod Video encoding from flv with ffmeg"
date: 2007-11-25
forum: Multimedia &amp; Video
---

### Post by Vaelrith on 2007-11-25
I'm having some trouble encoding video for the ipod.  I'm trying to use ffmpeg to encode a flv video such as those from youtube to a format suitable for the ipod.  I've trying to use the [ipodvidenc](https://help.ubuntu.com/community/iPodVideoEncoding?highlight=%28video%29%7C%28ipod%29#head-86df957b4e6f57ef3aceaf065506cfd92589766b) script, but when I do, I get this error...

```
Seems that stream 0 comes from film source: 1000.00 (1000/1) -> 29.97 (30000/1001)
Input #0, flv, from './Videos/longroadtoruin.flv':
  Duration: 00:04:29.8, bitrate: N/A
  Stream #0.0: Video: 0x0004, 29.97 fps(r)
  Stream #0.1: Audio: mp3, 44100 Hz, stereo
PIX_FMT_YUV420P will be used as an intermediate format for rescaling
Output #0, mp4, to '/home/nick/lrtr.mov':
  Stream #0.0: Video: mpeg4, yuv420p, 320x240, q=3-5, 700 kb/s, 29.97 fps(c)
  Stream #0.1: Audio: aac, 44100 Hz, stereo, 192 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec (id=0) for input stream #0.0
```

The file is still created, then when I try to open the file, I get the following error message (I attached the image of it since it was such a long error message).

If I open the file in text editor, it is empty.

---

### Post by newbe01 on 2007-11-25
Hello

I just bought an ipod touch and want to convert my music videos into m4k. Is this the flv format you're talking about or no?

Regards

---

### Post by Vaelrith on 2007-11-25
Flv I think, is flash format.  It is what youtube uses to display videos.

---

### Post by ron999 on 2007-11-25
Vaelrith, that script is not designed to accept an flv file as the input.
It's designed to accept an avi file as the input.
Try it yourself with an avi file.

---

