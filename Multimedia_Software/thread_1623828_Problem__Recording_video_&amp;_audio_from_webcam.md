---
title: "Problem : Recording video &amp; audio from webcam"
date: 2010-11-17
forum: Multimedia Software
---

### Post by remstereo on 2010-11-17
Hi all :)

I want to record myself to see the expression on my face on average through the USB webcam.
 
I use mencoder for recording from USB webcam .
 

```
mencoder tv:// -tv driver=v4l2:width=640:height=480:device=/dev/video0:forceaudio:adevice=/dev/dsp -ovc lavc -oac mp3lame -lameopts cbr:br=64:mode=3 -fps 16.2 -o test16.2.avi
```The problem is that the audio is not synchronized with the video. :confused:
 
what can i do ? help!:(

---

### Post by remstereo on 2010-11-23
up !!!!!!

---

