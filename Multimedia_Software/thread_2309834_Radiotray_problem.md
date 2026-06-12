---
title: "Radiotray problem"
date: 2016-01-13
forum: Multimedia Software
---

### Post by MibunoOokami on 2016-01-13
Happy new year everyone.
 

 I haven't used Radiotray in a while so can't give a specific time when this error occurred but the last time I used it was working perfectly fine. Now it doesn't want to stream any of the URLs I've added and spits out a long error message which in short mentions  gstdecodebin2.c(3576) and that no suitable codec is found.  
 

 Upon doing a search this seems to be a common problem that has one solution which is to install ubuntu-restricted-extras, however, I can verify that ubuntu-restricted-extras are already installed and up to date.
 I'm at a dead-end and wonder if anyone can offer another solution?

---

### Post by v3.xx on 2016-01-14
I haven't used radio-tray in a while either, but found a suggestion to add gstreamer0.10-ffmpeg.

[https://launchpad.net/~mc3man/+archive/ubuntu/gstffmpeg-keep?field.series_filter=trusty](https://launchpad.net/~mc3man/+archive/ubuntu/gstffmpeg-keep?field.series_filter=trusty)

Maybe?  I don't know for sure, just my guess.

---

### Post by MibunoOokami on 2016-01-14
> **v3.xx said:**
> I haven't used radio-tray in a while either, but found a suggestion to add gstreamer0.10-ffmpeg.

[https://launchpad.net/~mc3man/+archive/ubuntu/gstffmpeg-keep?field.series_filter=trusty](https://launchpad.net/~mc3man/+archive/ubuntu/gstffmpeg-keep?field.series_filter=trusty)

Maybe?  I don't know for sure, just my guess.

Thank you, that did the trick.

---

