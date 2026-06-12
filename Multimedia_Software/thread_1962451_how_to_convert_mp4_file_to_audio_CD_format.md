---
title: "how to convert mp4 file to audio CD format?"
date: 2012-04-21
forum: Multimedia Software
---

### Post by YigalB on 2012-04-21
I have MO4 video file (or flv).
How can I convert the audio into audio CD that can be played on good old CD player?

---

### Post by shantiq on 2012-04-21
not really worth doing as the sound quality will be thin


but if you must do it



```
ffmpeg -i file.mp4   file.wav
``` 

```
ffmpeg -i file.flv  file.wav
``` 

then burn:KS

---

