---
title: "Webcam doesn't work with Skype"
date: 2010-01-31
forum: Multimedia Software
---

### Post by Coco999 on 2010-01-31
I have difficulty with my webcam and Skype. I can see the other person but she can't see me. 
From a previous thread:

> Are you sure your camera isnt working? Supported hardware drivers are in the kernel usually.
Test: press alt+f2, type gstreamer-properties go to the video tab and see if your camera is listed as a device. If yes, press the test button.
This test was OK. I could see my face on the screen.

> Ah, the Skype camera thing...

Launch it this way:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
I tried this. It launches Skype OK, but the little window that should show what my webcam sees, appears full of black and white static.

What can I do?

---

