---
title: "Jerky divx/xvid playback after disabling swap"
date: 2009-08-07
forum: Multimedia Software
---

### Post by tlilja on 2009-08-07
I recently decided to remove my swap partition since there seemed to be no need for it. I have two GBs of RAM and its usage has never exceeded 900 MB. Now after the swap removal divx and xvid material "jerk" every 2-3 seconds. H264/AVC1 material plays fine, thanks to VDPAU.

My machine specs:
AMD Athlon X2 64 5000+
2 GB RAM
NVidia 9500GT

Running Kubuntu 9.04 with KDE 4.3 (from kubuntu-ppa).
Kernel version 2.6.30-020630-generic
Mplayer version SVN-r29325-4.3.3

Any suggestions as how to fix this?

---

### Post by HappyFeet on 2009-08-07
Put a small swap partition back on.

---

### Post by tlilja on 2009-08-08
Yep, after making a small swap file and activating it my problems were gone. Funny how everything else went as smoothly as ever without swap, but divx/xvid playback had problems.

---

