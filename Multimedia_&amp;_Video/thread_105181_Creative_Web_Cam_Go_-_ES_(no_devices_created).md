---
title: "Creative Web Cam Go - ES (no devices created)"
date: 2005-12-17
forum: Multimedia &amp; Video
---

### Post by pherseu on 2005-12-17
I'm trying to configure my CREATIVE WEBCAM GO at Ubuntu but the /dev/video* wasnt created.

My lsusb:
Bus 001 Device 003: ID 041e:4005 Creative Technology, Ltd WebCam Blaster Go ES

The correct modules are already loaded: ovcamchip and w9968cf.

A part of my lsmod:
w9968cf                67712  0
videodev                9344  2 spca5xx,w9968cf
ovcamchip              18568  0


But I still don't have a /dev/video0 or video device. All help is welcome!

---

