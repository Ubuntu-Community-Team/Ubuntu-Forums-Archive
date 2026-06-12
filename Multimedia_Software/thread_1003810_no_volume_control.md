---
title: "no volume control"
date: 2008-12-06
forum: Multimedia Software
---

### Post by dmancini on 2008-12-06
let me start for apologizing for my lack of knowledge.  I am an absolute noob.  

I am having trouble with my volume control.  the only way that I can control it is through my actual speakers.  I have an audigy soundblaster which ?seems? to be configured correctly.  I have uninstalled and reinstalled the volume control applets.  But nothing.  It shows the icons for volume and that they are changing but alas no volume control. I am sure it is something simple I have configured incorrectly.  I am running ubuntu 8.04.

If I am posting incorrectly or this issue has been solved elsewhere please let me know.

---

### Post by jlfallaw on 2008-12-13
> **dmancini said:**
> let me start for apologizing for my lack of knowledge.  I am an absolute noob.  

I am having trouble with my volume control.  the only way that I can control it is through my actual speakers.  I have an audigy soundblaster which ?seems? to be configured correctly.  I have uninstalled and reinstalled the volume control applets.  But nothing.  It shows the icons for volume and that they are changing but alas no volume control. I am sure it is something simple I have configured incorrectly.  I am running ubuntu 8.04.

If I am posting incorrectly or this issue has been solved elsewhere please let me know.

I had the same problem. What I had to do was right-click on the Volume Control icon and choose Preferences. When it asks what device to control, I selected Alsa mixer and clicked PCM as the line to control with the volume buttons. You may have to just play around with it, but for me, nothing but PCM works.

---

