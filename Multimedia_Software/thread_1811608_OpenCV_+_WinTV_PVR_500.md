---
title: "OpenCV + WinTV PVR 500"
date: 2011-07-25
forum: Multimedia Software
---

### Post by Noxville on 2011-07-25
Hi all.

I'm attempting to use the OpenCV library with a TV Capture Card (Hauppauge WinTV PVR 500). 

I've generated Haar Cascades for what I need, and I've tested them using a WebCam and they work perfectly.

I'm now trying to use my Capture Card instead of the WebCam. I believe OpenCV works with the V4L drivers fine (from what Googling reveals), but I don't have a V4L device block for my capture card.

Heres my v4l-info:
[http://pastebin.com/CNzNTDPh](http://pastebin.com/CNzNTDPh)

I can ```
vlc v4l2:///dev/video32
``` perfectly, but I can't seem to find any reference to using this capture card with OpenCV.

Any examples/solutions would be awesome (preferably example code in C/C++).

It's likely I'm just looking in completely the wrong place.

---

