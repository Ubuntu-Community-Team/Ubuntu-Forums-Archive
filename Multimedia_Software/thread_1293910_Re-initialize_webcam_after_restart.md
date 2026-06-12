---
title: "Re-initialize webcam after restart?"
date: 2009-10-17
forum: Multimedia Software
---

### Post by garthoverman on 2009-10-17
Here's the summary of my problem:

I have a logitech Quickcam and it ordinarily it works fine (with Skype, its primary purpose on my machine). It does have this one little glitch, however.

It only seems to work if I connect the camera to my USB port once the OS has booted. If I leave the camera connected and reboot, it does not seem to initialize the camera. Usually, when this happens, I merely have to disconnect and re-connect the camera and it works just fine after that.

This has really become an annoyance for me however, and I'm looking for a way to ensure that my camera is initialized properly with each reboot, or at the very least a command I can enter on the command line to initialize it.

Ordinarily the camera is /dev/video0, and /dev/video0 continues to appear in the /dev folder, however modprobe /dev/video0 returns FATAL: Module /dev/video0 not found.

I'm not THAT much of a linux newbie, but I'm no expert by any means either. I suspect there is something stupid I'm overlooking and I hope someone can point out what that is.

Thanks in advance.

---

