---
title: "Logitech Quickcam Connect - VLC &amp; Blue Hue"
date: 2007-06-03
forum: Multimedia &amp; Video
---

### Post by Hoshimaru on 2007-06-03
Good evening...

I've been trying to set up VLC for streaming my webcam. Unfortunately, I get a bue hue and I don't know how to get rid of it.
When it's being used by Camorama the colours are perfect. With spcagui I've to click the colour correction button.

After searching google, someone suggested using gstreamer-properties and set the Video Output to custom and use this option:
```
ffmpegcolorspace ! video/x-raw-yuv,format=(fourcc)YV12 ! xvimagesink
```
Based on the reactions this seemed to have helped lots of people.
Unfortunately for me, it f**ails to initialize Xv**.

Xorg runs on the fglrx driver, as my laptop comes with a Mobility Radeon 9700.

Has the Xv failure something to do with the fglrx drivers?

And I was wondering if there's a VLC setting to use that 'Colour Correction' feature spcagui and kopete have in common.
[[IMG]http://img453.imageshack.us/img453/873/screenshotvlcmediaplayexm0.th.png[/IMG]](http://img453.imageshack.us/my.php?image=screenshotvlcmediaplayexm0.png)

I look forward to hearing from you :)

---

