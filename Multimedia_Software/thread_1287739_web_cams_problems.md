---
title: "web cams problems"
date: 2009-10-10
forum: Multimedia Software
---

### Post by hawkeyeRO on 2009-10-10
I just installed 9.04 on my Dell Inspiron 1545 laptop, and tried to set up both my webcams with, but I had no success. 

The 1st webcam is a Creative WebCam Pro, which is detected (based on the logs) by the system as: ov511: USB OV511+ video device found / ov511: model: Creative Labs WebCam 3 / ov511: Sensor is an OV7620. Using lsubs, gets the following info: ID 05a9:a511 OmniVision Technologies, Inc. OV511+ WebCam.

The 2nd webcam is a Creative Live! Cam Video IM Pro, with the ID 041e:4055 Creative Technology, Ltd Live! Cam Video IM Pro. From what I read on different blogs, this model does not seem to have a Lunix driver...

The logs only contain info about the 1st cam and it is also the only one that has the led on after connecting it to the laptop. There is a /dev/video0, and based on this blog: [http://alpha.dyndns.org/ov511/install.html](http://alpha.dyndns.org/ov511/install.html), it means that the driver exists. My assumtion is that it corresponds to the OV511+ WebCam, but I'm not sure how to verify this and how to make it actually work.

Any help/suggestion is very much appreciated,
H.

---

### Post by user333 on 2009-10-10
I found out that you don't need drivers for web-cams. You just need a program that will take it.  I was able to make mine work on Pitivi (a movie editor), but nothing else. It might be that some of your programs aren't able to use your web-cam :( I hope that you can get them working.

---

