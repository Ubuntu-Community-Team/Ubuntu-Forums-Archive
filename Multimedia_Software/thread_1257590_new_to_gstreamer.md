---
title: "new to gstreamer"
date: 2009-09-04
forum: Multimedia Software
---

### Post by co.sam on 2009-09-04
Hi friends, 
Hope you are doing great.Recently i started reading gstremer to play around with media files but I am absolutely new to gstreamer. 
 
I refered an application manual of gsteamer.Also i tried some gst-launch examples such as: 
 
1.gst-launch audiotestsrc ! audioconvert ! audioresample ! osssink(plays sound) 
 
2.gst-launch-0.10 ximagesrc num-buffers=1 ! ffmpegcolorspace ! pngenc ! filesink location=screenshot.png(captures the screen shot) 
 
Though I have tried these examples I have not understood the exact meaning of what these individual elements of this pipeline are donig and also how come these pipelines are constructed in this particular order. 
 
Please help in out to learn gstremer 
Any kind of help is welcome....... 
 
regards, 
co.sam

---

