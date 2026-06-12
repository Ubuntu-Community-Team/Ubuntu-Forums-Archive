---
title: "Sluggish video and desktop effects...fixed by running glxgears"
date: 2007-06-24
forum: Multimedia &amp; Video
---

### Post by Mxo on 2007-06-24
Hello everybody

I have Ubuntu 7.04 running on a laptop with an intel915gm graphic card and video playback as well as a lot of other graphic-things run very sluggish (scrolling is unbearably jumpy and slow). I tried running glxgears in order to find out if it was due to a driver issue, but the framerate was okay (about 600fps, not great, but...well its a intel900).

But I realized a very strange effect: while glxgears is running video playback and scrolling work perfectly. So right now I have glxgears running in the background when browsing or watching a video. Still I think this not to be a real fix to the problem and I would really like to find a solution that doesn't require a app constantly running in the background.

Computer: Asus A3E, Pentium M 1.6 GHz, 512 MB shared ram, 60 GB harddrive....

Thanks for helping to explain this strange behaviour
  Stephan

---

### Post by Ziox on 2007-06-24
check to make sure that direct rendering is enabled:

glxinfo | grep direct

also, check the command with and without glxgears running.

---

### Post by Mxo on 2007-07-11
Direct Rendering is enabled, with and without glxgears running.

---

### Post by Mxo on 2007-07-26
I just realized that everything runs smooth once I plug out the power cord and run on batteries. It seems somehow to be linked to power-management. The CPU-settings have no influence though (setting dynamic/powersave/performance), only plugging out the power cord.
Any help?
Thanks in advance

Stephan

---

