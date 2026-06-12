---
title: "How to record ffmpeg in higher quality?"
date: 2013-06-10
forum: Multimedia Software
---

### Post by Predictability on 2013-06-10
I'm trying to record some touhou gameplay using ffmpeg.  But 480p is too low quality.  So my question is, How can I record a 640x480 screen area at a higher quality than 480p?

---

### Post by shantiq on 2013-06-11
all size options with -s   found in  > man ffmpeg   anything after   -s vga   is larger than 480p

> -s size
Set frame size. The format is wxh (ffserver default = 160x128, ffmpeg default = same as source). The following abbreviations are recognized:
sqcif
128x96
qcif
176x144
cif
352x288

4cif
704x576
16cif
1408x1152
qqvga
160x120
qvga
320x240
vga
640x480

svga
800x600
xga
1024x768

uxga
1600x1200
qxga
2048x1536
sxga
1280x1024
qsxga
2560x2048
hsxga
5120x4096
wvga
852x480
wxga
1366x768
wsxga
1600x1024
wuxga
1920x1200
woxga
2560x1600
wqsxga
3200x2048
wquxga
3840x2400
whsxga
6400x4096
whuxga
7680x4800
cga
320x200

ega

640x350

hd480
852x480
hd720
1280x720
hd1080
1920x1080

---

