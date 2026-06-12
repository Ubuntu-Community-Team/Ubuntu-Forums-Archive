---
title: "Intel HD 4000 Improving Performance"
date: 2012-11-25
forum: Multimedia Software
---

### Post by Dustpaw on 2012-11-25
I'm running on a lenovo x230 tablet PC that has  build in Intel HD 4000 (Ivybridge) and I was wondering if there was anything I can do to improve my graphics performance.   I'm running on Quantal (12.10)

I've recently added:
Section "Device"
 Identifier "Card0"
 Driver "intel"
 Option "AccelMethod" "sna"
EndSection

To my XORG.conf file but I was looking for other ways to improve performance.  The build in graphics processor looks like its limited to 256 memory, is there a way to increase that through settings?  Would increasing it improve performance?

---

