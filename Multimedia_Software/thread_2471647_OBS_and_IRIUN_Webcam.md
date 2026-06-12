---
title: "OBS and IRIUN Webcam"
date: 2022-02-05
forum: Multimedia Software
---

### Post by ov10fac on 2022-02-05
I am trying to use OBS Studio in conjunction with IRIUN webcam on my Ubuntu 20.04 desktop PC.  Both applications work fine by themselves and with other applications like Teams and Zoom.  However when I try to use OBS Virtual Camera and Iriun the IRIUN display turns to a green pixelated screen.  I think both Virtual Camera and Iriun are using the same V4l2loopback device (/dev/videoxx).  I have posted this issue with the OBS community but they have not been able to determine any solutions.  I hope that this larger forum might have some ideas that I can try to resolve this issue.

Thanks for any advice you can provide.

---

### Post by ov10fac on 2022-02-11
Bump

---

### Post by Autodave on 2022-02-12
When you open OBS, bottom left of screen: under Sources.....what does it list for video device?

Have you tired clicking on the video device and then the gear icon (settings) and tried adjusting anything there?

---

### Post by ov10fac on 2022-02-12
It lists my USB web cam and the iriun web cam.  Everything is fine until I activate the OBS Virtual Camera.  Form what I have been able to find, it looks like both OBS Virt Cam and Iriun are using the same loopback device.  I thank that's legal, but there must be some kind of compatible issue between Virt Cam and Iriun.

---

