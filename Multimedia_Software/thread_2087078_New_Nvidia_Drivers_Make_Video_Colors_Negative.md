---
title: "New Nvidia Drivers Make Video Colors Negative"
date: 2012-11-22
forum: Multimedia Software
---

### Post by amtur_poet on 2012-11-22
I recently installed the new drivers released by Nvidia to complement Steam for Linux's release, and everything seems to run fine, except for one thing. When I try to stream a video through the web browser now, all the colors are negative, and the resolution looks to be lower than normal. Is there a way to fix this?

---

### Post by JohnnyVW on 2012-11-22
> **amtur_poet said:**
> I recently installed the new drivers released by Nvidia to complement Steam for Linux's release, and everything seems to run fine, except for one thing. When I try to stream a video through the web browser now, all the colors are negative, and the resolution looks to be lower than normal. Is there a way to fix this?


I've had this happen before on Flash video (YouTube).  Right-click the video, click "Settings" and un-check "Enable Hardware Acceleration."

---

### Post by SeijiSensei on 2012-11-23
It's not NVIDIA's fault.  Adobe introduced this bug into flashplayer right before they discontinued Linux development, and now, of course, they won't fix it.

---

### Post by TenPlus1 on 2012-11-23
I would recommend using Google Chrome as your browser because it comes with PepperFlash built in and is a newer version than the one installed on Ubuntu...  This fixes the bluish tiny on movies...

---

### Post by efflandt on 2012-11-23
Note that regular flash has to be full screen to change any settings (like to disable hardware acceleration). If it is not full screen, the settings dialog will hang.

---

### Post by ratdog on 2012-12-01
Thanks for this!  I've been watching blue people on youtube for about a year now.

btw, YouTube is the only site I had this problem on.  Every other site played videos just fine.  Even YouTube videos through Facebook.

---

### Post by SeijiSensei on 2012-12-02
That's because not many sites actually invoke hardware acceleration in Flash (it requires special code to use something Adobe calls "Stage Video"), but YouTube does.

---

