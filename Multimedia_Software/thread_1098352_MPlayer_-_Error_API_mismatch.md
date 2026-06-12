---
title: "MPlayer - Error: API mismatch:"
date: 2009-03-16
forum: Multimedia Software
---

### Post by ffixcollector on 2009-03-16
I get this error when trying to use mplayer from the command line:

```
Error: API mismatch: the NVIDIA kernel module has version 180.29,
but this NVIDIA driver component has version 180.37.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
Error 1 at libvo/vo_vdpau.c:258

```
When running Smplayer, or Gmplayer, videos play, except there is slight screen tear in mostly fast action scenes. MPlayer also seems to drop frames, even though frame dropping is not enabled, and the video lags during action scenes causing audio/video synchronization issues. 

I just uninstalled NVIDIA-Linux-x86_64-180.29-pkg2.run. It recompiled the kernel and reconfigured xorg. There where several errors during the install, but I do not know how to access the log to post them. The errors do not show up if I install nvidia-180-libvdpau. I also did a sudo apt-get --purge remove nvidia-glx, but it did not remove anything.

I'd like to get the screen tear figured out, because video is the only thing windows xp seems to work better for.

---

### Post by ffixcollector on 2009-03-17
I just installed nvidia 180.37. That fixed the API mismach, but there is still frame drops, lag, and screen tear.

---

### Post by ffixcollector on 2009-03-17
does anyone have any ideas??

---

