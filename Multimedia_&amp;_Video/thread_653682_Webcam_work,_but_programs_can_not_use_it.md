---
title: "Webcam work, but programs can not use it"
date: 2007-12-30
forum: Multimedia &amp; Video
---

### Post by TTL on 2007-12-30
Hello,
I would like to use my webcam for a video chat. The good thing is, the camera gets detected and the zr364xx driver is loaded. I can directly copy an image from the video device (this will overwrite a file test.jpg in the current directory without asking) with:

dd if=/dev/video0 of=test.jpg bs=1M count=1

and the resulting image shows me what is infront of the camera, so the camera works.
Unfortunately every program I tried tells me that eiter it can not open /dev/vidoe0 or that the requested resolution is not supported. I tried:
xawtv: ioctl: VIDIOC_S_STD(std=0x0 []): Invalid argument no way to get: 384x288 32 bit TrueColor (LE: bgr-)
camorama: Could not connect to video device (/dev/video0) Please check connection.
Ekiga: Error while opening /dev/video0 Your video driver doesn't support the requested video format.

If I capture a test picture with the method above I get a 320x240 jpg. I am using Kubuntu 7.10 with a Concord Eye Q Duo 1300 (should be the same as a Ricoh RDC-6000)

Any ideas?

---

