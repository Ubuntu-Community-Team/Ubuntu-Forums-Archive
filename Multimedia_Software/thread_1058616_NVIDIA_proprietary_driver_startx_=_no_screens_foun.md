---
title: "NVIDIA proprietary driver: startx = no screens found"
date: 2009-02-03
forum: Multimedia Software
---

### Post by GoofusGreen on 2009-02-03
Graphics hardware is 2x NVIDIA GTX 260's
Ubuntu 8.10 64-bit

I tried the Ubuntu-packaged binary driver as well as the newer version from nvidia.com.

Driver installs fine, but when I try to startx, I get a "fatal server error: no screens found" and no graphics for me, just text.

Among the things I have found: (will try in the morning)

Try "depmod -a" after startx fails
Add "UseDisplayDevice" "DFP" to xorg.conf Device section (very old, dunno if I'll try it.)
nvidia-xconfig

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/313938](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/313938) (looks promising)



**EDIT** I follows what was posted in the bug, that is, making entries in xorg.conf with PCI Bus ID for my two graphics cards. Works good now.

Now, how do I get 3 monitors in TwinView? Right, nermind. Xinerama ftw.

---

### Post by MrCharles on 2009-02-05
I'm amazed at this issue.
You'd think an OS upgrade would account for something as necessary as video drivers working properly - even if they are proprietary.

---

