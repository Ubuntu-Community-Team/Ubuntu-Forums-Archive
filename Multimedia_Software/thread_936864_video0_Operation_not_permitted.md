---
title: "video0: Operation not permitted"
date: 2008-10-03
forum: Multimedia Software
---

### Post by tramontano on 2008-10-03
Hi all,

I have an old HP notebook running on Hardy, and a (very) old USB webcam recognized as "ST*-something*". Every time I connect the webcam, the system recognizes it, creates the /dev/video0 device, and asks if I want to copy its images to computer. So far, so good. 

My problems:

a) When I first open any webcam software (except XawTV), it will say that "/dev/video0 is not available";

b) Opening XawTV (without any config files) works; Any webcam software opened after this will work as well...

c) By any means I can get MPlayer working with the webcam. The typical command "mplayer tv:// -tv driver=v4l" (and all its variations, including changing to v4l2 driver) won't work. The message is simply "/dev/video0: Operation not permitted". 

Now... what the f*** does this "operation not permitted" thing means? :confused:

Tried almost everything... any ideas? 

Thanks !!

---

