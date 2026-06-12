---
title: "logitech pro 5000, UVC driver problem"
date: 2007-06-01
forum: Multimedia &amp; Video
---

### Post by Houman on 2007-06-01
hi everyone;

I have recently acquired a refurbished logitech 5000 webcam and I tried 
using it with the uvc drivers. The problem is that ekiga and amsn can 
use it perfectly after i install the uvc drivers. However, when i try to 
load it using gstreamer-properties the video shown is garbled. The odd 
thing is that on top of the video there is a small strip of pixels which 
are perfectly fine (if i move my hand in front of the webcam I can see 
it in that small strip) but the majority of the picture is just noise.

I need to be able to use gstreamer with this webcam because the 
application that I need to use doesn't support v4l2 but it supports the 
gstreamer framework (so I assume it can read v4l2 video through 
gstreamer). Any help will be much appreciated.

( I posted this to the devel site for uvc, sorry for double posting, but i thought  someone here might also have the solution)

regards

Houman

---

