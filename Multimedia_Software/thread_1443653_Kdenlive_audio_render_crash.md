---
title: "Kdenlive audio render crash"
date: 2010-03-31
forum: Multimedia Software
---

### Post by alex4c on 2010-03-31
I started to use KDEnlive 0.7.5 which is very nice program for video editing but I've encountered a problem. In a rendering dialogue when I tick export audio and try to render it this error appear: 
>  Rendering of /home/alex/kdenlive/untitled4.mp4 crashed
 consumer_avformat.c: audio codec libfaac unrecognised - ignoring
consumer_avformat.c: Unable to encode audio - disabling audio output. [mp4 @ 0xbca420]track 1: codec frame size is not set
I tried with .ogg, .mp3 and .wav file format but I got the same message. 
If anyone has any idea what is wrong it would be appreciated.

---

### Post by alex4c on 2010-03-31
Maybe some kind codec problem?
Anyone?

---

### Post by guneza on 2010-04-09
I had the same problem, and I got it to work with the libmp3lame on KDENlive 0.75.

Here are the settings I used:

f=mp4 acodec=libmp3lame ab=128k ar=44100 vcodec=libx264 minrate=0 b=3000k s=640x480 aspect=%dar mbd=2 trellis=1 mv4=1 pass=2

---

### Post by alex4c on 2010-04-09
Thanks a lot, it works now. It was libmp3lame that got it working.

---

