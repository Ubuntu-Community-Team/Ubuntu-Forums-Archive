---
title: "Using avconv to extract image frames from a movie"
date: 2012-07-02
forum: Multimedia Software
---

### Post by silviutp on 2012-07-02
Hi,

I'm trying to extract frames from movies that I've recorded on my Desktop using HyperCam (a video capture software on Windows ).

I used avconv to do this and it is ok when I extract all frames with the command:
```
$ avconv -i file.avi -f image2 Out%00d.jpg

```

However, I want to extract say one frame per second with the "-r" option but this does not work...

```
silviu@silviu-pc:~/REC/pics.out$ avconv -i ../s1-formare.avi -r 1 -f image2 Out%00d.jpg
avconv version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:52:09 with gcc 4.6.3
Input #0, avi, from '../s1-formare.avi':
  Duration: 00:10:43.60, start: 0.000000, bitrate: 961 kb/s
    Stream #0.0: Video: msvideo1, rgb555le, 640x480, 5 tbr, 5 tbn, 5 tbc
    Metadata:
      title           : HyperCam Video
Incompatible pixel format 'rgb555le' for codec 'mjpeg', auto-selecting format 'yuvj420p'
[buffer @ 0x1818320] w:640 h:480 pixfmt:rgb555le
[avsink @ 0x1817340] auto-inserting filter 'auto-inserted scaler 0' between the filter 'src' and the filter 'out'
[scale @ 0x181d8a0] w:640 h:480 fmt:rgb555le -> w:640 h:480 fmt:yuvj420p flags:0x4
Output #0, image2, to 'Out%00d.jpg':
  Metadata:
    encoder         : Lavf53.21.0
    Stream #0.0: Video: mjpeg, yuvj420p, 640x480, q=2-31, 200 kb/s, 90k tbn, 1 tbc
    Metadata:
      title           : HyperCam Video
Stream mapping:
  Stream #0:0 -> #0:0 (msvideo1 -> mjpeg)
Press ctrl-c to stop encoding
[mjpeg @ 0x18168e0] Error, Invalid timestamp=0, last=0
Video encoding failed

```

When I use the "-r" option with a value lower than the actual framerate (5fps) of the input movie I get the same error.

Can someone help with this, please ? Or a suggestion for another program...

---

### Post by shantiq on 2012-07-02
---------------------------yes sorry i had not seen the second half of your question

so     > mplayer -ao null -vo png input.file   only gives you what you already have...........

---

### Post by silviutp on 2012-07-02
> **shantiq said:**
> ---------------------------

I can do this also with avconv. What I need is to extract 'some' images, say one per sec or one at 2 secs.

No I observed that it works with ffmpeg. I didn't use ffmpeg for the first time because I saw that it's deprecated... but avconv doesn't work for the example I've given in the previous post and ffmpeg works.

---

### Post by kcmichaelb on 2012-07-13
This is what I use and it works for me without any errors:

avconv -i ***videofile.avi*** -vsync 1 -r 1 -an -y '***videofolder/videoframe***%d.bmp'

Replace the bold text with your file/folder/frame names.

---

### Post by kcmichaelb on 2012-07-13
The example I posted has .bmp but it also works with .jpg.

---

### Post by czunino on 2012-08-30
For me works very well
thx

---

### Post by silviutp on 2012-09-07
thank you, your example works

---

