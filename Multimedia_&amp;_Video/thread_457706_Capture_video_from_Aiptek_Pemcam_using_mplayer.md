---
title: "Capture video from Aiptek Pemcam using mplayer"
date: 2007-05-28
forum: Multimedia &amp; Video
---

### Post by uboltun on 2007-05-28
I have invested some time on this one and since I didn't find a "google' solution this is what I did.

1. Recompiled mplayer from source. 
2. To display webcam run

mplayer tv:// -tv driver=v4l:device=/dev/video:outfmt=rgb24 -flip

The trick is the option outfmt=rgb24 , for some reason mplayer set it wrong and so I saw just a green picture.
My hardware:

lsusb | grep -i pencam
Bus 002 Device 002: ID 0553:0202 STMicroelectronics Imaging Division (VLSI Vision) Aiptek PenCam 1

---

