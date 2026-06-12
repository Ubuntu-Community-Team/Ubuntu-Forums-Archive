---
title: "Black screen on login if second monitor unplugged"
date: 2014-08-26
forum: Multimedia Software
---

### Post by Drakmor on 2014-08-26
Hey all, my second monitor died, and when I tried to remove it, I ran into a problem (which I've had for a long while, its just never been an issue since I haven't needed to leave it unplugged): System boots up fine, but when I log in, if the second monitor is not plugged in, I get a black screen a few seconds into the splash screen. I can still access virtual terminals, and I hear music starting so I know the system is logging in. As soon as I plug the monitor back in, everything shows up, and if I unplug the monitor after logging in, it goes black. I

I've tried re-running nvidia-xconfig, not using an xorg.conf file at all, and adding Option "UseDisplayDevice" "DFP" (as detailled in [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)) doesn't seem to do anything. At one point, I managed to get logged in without it plugged in, but only had one (incorrect) resolution, and as soon as I fixed the nvidia driver it broke again... leading me to think it may be driver related. The second monitor is marked as off in nvidia-settings and kubuntu's settings.

I'm currently running Kubuntu 14.04 with a Nvidia 560 ti graphics card, and using the nvidia-331 331.38 driver. 

Thanks in advance!

---

