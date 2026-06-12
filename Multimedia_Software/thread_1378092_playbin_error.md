---
title: "playbin error"
date: 2010-01-11
forum: Multimedia Software
---

### Post by shariefbe on 2010-01-11
Hello,
        how to play with "playbin". when i try to play the video with playbin i am getting this error 
```
root@freescale ~$ gst-launch playbin uri=/root/yuvraj.mp4 
Setting pipeline to PAUSED ...
ERROR: Pipeline doesn't want to pause.
ERROR: from element /GstPlayBinlaybin0: Invalid URI "/root/yuvraj.mp4".
Additional debug info:
gstplaybasebin.c(1674): gen_source_element (): /GstPlayBinlaybin0
Setting pipeline to NULL ...
FREEING pipeline ...
root@freescale ~$

``` Now i am standng still. It is telling as invalid URI. But the video is in that PATH only. Then how to use this gen_source_element() function? how to implement it? please help me..

---

