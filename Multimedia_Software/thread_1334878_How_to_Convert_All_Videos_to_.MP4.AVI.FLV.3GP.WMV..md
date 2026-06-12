---
title: "How to Convert All Videos to .MP4/.AVI/.FLV/.3GP/.WMV/.MOV/.MPG/.RM/.RMVB/.MKV/.VOB……"
date: 2009-11-22
forum: Multimedia Software
---

### Post by regttey on 2009-11-22
Nowadays, people have so many kinds of portable music/video players, and they play different video formats, so how to convert video from one popular video format to another is a question. Now I will give you a excellent total video converter: 

for more information,please go to 

[http://www.murga-linux.com/puppy/viewtopic.php?p=364691#364691](http://www.murga-linux.com/puppy/viewtopic.php?p=364691#364691)

---

### Post by Uncle Spellbinder on 2009-11-22
Thanks for the link to a Puppy Linux forum login page. Nice.
A real help indeed.

:roll:

---

### Post by drobi on 2010-01-04
I need an avi to rm/rmvb (avi>rmvb, avi2rmvb) converter too in Koala. Help me someone! i don't need other solution, just a simple convert method.

---

### Post by howefield on 2010-01-04
> **drobi said:**
> I need an avi to rm/rmvb (avi>rmvb, avi2rmvb) converter too in Koala.

Not sure how well this works although it seems to on my tests.

Install mplayer & w32codecs if you haven't already got them.

```
sudo apt-get install mplayer
```

Get w32codecs from [http://packages.medibuntu.org/](http://packages.medibuntu.org/)

Then in terminal try something like this.

```
 mencoder test.avi -oac mp3lame -lameopts preset=128 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1200 -ofps 25 -of avi -o test.rmvb
```

Substitute "test.rmvb" and "test.avi" with the name your files.

Also, usually better to start your own thread.

---

### Post by drobi on 2010-01-04
Thank you, you are right. It seems working.
But!!

WARNING: OUTPUT FILE FORMAT IS _AVI_. See -of help.
success: format: 0  data: 0x0 - 0xb15c800
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  640x480  12bpp  25.000 fps  946.1 kbps (115.5 kbyte/s)
[V] filefmt:3  fourcc:0x44495658  size:640x480  fps:25.000  ftime:=0.0400
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 160.0 kbit/10.42% (ratio: 20000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
MP3 audio selected.
VDec: vo config request - 640 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
videocodec: libavcodec (640x480 fourcc=34504d46 [FMP4])
Writing header...1f ( 0%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

(Sorry for the wrong place.)
The result called rmvb but its avi althought, is biger, then the orginal avi it means, the result really not rmvb.
I will open a new post. you are right.

---

