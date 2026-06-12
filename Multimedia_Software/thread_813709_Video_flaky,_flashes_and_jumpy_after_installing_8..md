---
title: "Video flaky, flashes and jumpy after installing 8.04"
date: 2008-05-31
forum: Multimedia Software
---

### Post by bkly-dog on 2008-05-31
Video (including the desktop and windows) has been funky ever since I upgraded from 7.10 to 8.04. 

There are little glitches every few seconds whenever there is movement on the screen, including videos playing or scrolling in the web browser. Watching flash videos can be very irritating. Trying to scroll a large web page using the arrow keys is also annoying. I also notice that a lot of cpu is being eaten (80%+) just by watching a small flash video (and then cpu stays high afterward often).

Usually the glitches happen only to the selected window that I'm scrolling or that's playing a video, but occasionally the whole desktop gets into a funk--every 10 seconds or so the bottom half of the screen flashes black for a few milliseconds.

I'm on x86_64 with an nvidia GeForce 7600 video card. nvidia-glx-new is installed as the driver. I see mesa stuff installed as well (should it be?). I'm using the Firefox 3 b5, but I had to do some work to get flash videos running in it. CPU is core 2 duo, 1.83 GHz.

One oddity: GLX seems to be running, but when I do compiz --replace, I get:

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0398 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
```

A LOT is working--I have all the compiz stuff running, etc.

Thanks for your help. Sorry, I'm new to this.

---

