---
title: "Problem with NVidia proprietary drivers"
date: 2007-07-07
forum: Multimedia &amp; Video
---

### Post by Fisher on 2007-07-07
Hi there!
   I just installed the NVidia proprietary drivers sucessfully, but, every time I reboot, I cannot get into graphics mode because it says the kernel module is from a different version, so , I end up reinstalling the driver and everything works fine, until I reboot, get the same error and need to reinstall again.
   Any sugestions?? My card is a MX-440  agp 4x.

---

### Post by RomeReactor on 2007-07-07
Hi. I'm not sure if this is what you're missing, but perhaps you don't have **nvidia-kernel-common** installed. you can find it through Synaptic, or from the terminal (Applications->Accessories->Terminal):
```
sudo apt-get install nvidia-kernel-common
```

---

### Post by calraith on 2007-07-07
This might help:

[http://ubuntuforums.org/showthread.php?t=459771](http://ubuntuforums.org/showthread.php?t=459771)

---

