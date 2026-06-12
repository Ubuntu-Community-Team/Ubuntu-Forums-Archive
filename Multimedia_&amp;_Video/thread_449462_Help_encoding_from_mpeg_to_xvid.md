---
title: "Help encoding from mpeg to xvid"
date: 2007-05-20
forum: Multimedia &amp; Video
---

### Post by electro93 on 2007-05-20
Hey all,

I've been working on this for sometime googling / testing my own methods, but I've been unsuccessful (partially) in encoding an mpeg -> xvid.

I am currently using the following method:

mencoder $file -ovc xvid -xvidencopts bitrate=1000:aspect=1.333 -vf pp=lb -oac mp3lame  -lameopts fast:preset=standard -o $file.avi

It encodes just fine, but when I play it on my TV using a DVD player, its auto set to 640x480 so I have black lines on either side of my tv.  Zooming on the TV and changing the aspect on the DVD player do nothing.  However, when I play the mpeg, its at fullscreen.

Is there a way to encode the mpeg into xvid but have it display at full screen on the DVD player?

Thanks,

JB

---

### Post by robertrej on 2007-05-21
As a  new comer to mencoder or ffmpeg I am trying to figure out how to improve the quality
of my video's  I downloaded from video google.I have been following all the instructions
from the various web sites I find on the two software programs mentioned above but it never really seem to improve the quality of the videos very much .So I guess the real question is 
can one take a medium quality video and really improve the appear that much ?
I am not really concerned with file size or even processing time just quality!



                                                    Any ideas would be great /Thanks
                                                     Bob

---

### Post by NumPy on 2007-05-21
Honestly the answer is going to be no. Simply because we use lossy formats. In this the files (images, audio, video) suffer from generation loss. Due to repeatedly compressing and decompressing the file. This causes the file to progressively lose quality.

J.B Im sure you have looked, but give ffmpeg a try. Its what I use and allows you to set the PAL/NTSC Values according to your viewing pleasure.

---

### Post by electro93 on 2007-05-22
I tried FFmpeg, but for some reason my DVD player cannot read the default xvid encoder (FFMPEG XVID).  The Sound plays but I get no video.  Works fine and perfectly on a PC though.  Is there a way to have FFMPEG use an xvid 4.0 codec?

thanks!

---

### Post by NumPy on 2007-05-24
There is, im not sure how to impliment it in (k)Ubuntu though.. I compiled from source using 
```
/FFMpeg-*/configure  --enable-mp3lame --enable-faac --enable-faad --disable-ffserver --disable-ffplay --enable-small --enable-memalign-hack --enable-gpl --enable-xvid --enable-vhook --enable-pthread

```

I doubt this will help you at all seeing as you probably used apt to grab ffmpeg.  But I thought I would share.

---

