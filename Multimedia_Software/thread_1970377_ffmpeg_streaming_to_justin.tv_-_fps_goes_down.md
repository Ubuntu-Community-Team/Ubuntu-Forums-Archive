---
title: "ffmpeg streaming to justin.tv - fps goes down"
date: 2012-05-01
forum: Multimedia Software
---

### Post by Halbblutplins on 2012-05-01
I want to stream my desktopsession to justin.tv. Therefore I use ffmpeg:

```
#!/bin/bash
API_KEY="live_*****************"
FPS="30"

INRES='1920x1080'
OUTRES='720x480'

ffmpeg -f x11grab -s "$INRES" -r "$FPS" -i :0.0 \
       -f alsa -i pulse -vcodec libx264  -s "$OUTRES"  \
       -acodec libmp3lame -ab 64k -ar 22050 -threads 0 \
       -f flv "rtmp://live.justin.tv/app/$API_KEY"
exit
```but after a while I have only ca. 9fps.

Hope someone will be able to help me.

---

### Post by FakeOutdoorsman on 2012-05-01
Please provide a plain, unscripted ffmpeg command and the complete console output.

---

### Post by Halbblutplins on 2012-05-08
I want to do, but I don't know what it means " .... provide a plain, unscripted ffmpeg ..." (I'm German and 14).

Look forward to your reply!

---

