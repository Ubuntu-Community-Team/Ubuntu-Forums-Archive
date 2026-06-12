---
title: "Miro segmentation error when playing"
date: 2008-10-18
forum: Multimedia Software
---

### Post by wangjiajun on 2008-10-18
Hi, I just installed Miro on my Hardy.

It is working good until playing. I can download, search as normal. However, once I click to play a downloaded video, Miro exits saying "segmentation fault".

Any idea how to tackle this down?

Thanks!

---

### Post by pacopepelaz on 2008-11-09
Try changing the renderer:
open miro
go to video->options->video playback 
change the renderer from xine (which is, I think, the default) to gstreamer

---

