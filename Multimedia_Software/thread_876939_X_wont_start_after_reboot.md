---
title: "X wont start after reboot"
date: 2008-08-01
forum: Multimedia Software
---

### Post by jasonlfunk on 2008-08-01
I tried to update my nvidia drivers, but now X will not start after I reboot it. Sometimes I manage to get it working by reinstalling the drivers but not all the time, and if I get them working, they do not stay working - just until I reboot. Here is the error message I get:
```
Error: API mismatch: the NVIDIA kernel module has version 71.86.04,
but this NVIDIA driver component has version 169.12.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

---

### Post by mocha on 2008-08-01
seems like you have nvidia-glx-new and nvidia-glx somehow mixed up.  I would search synaptic for nvidia- and uninstall  all the drivers and then reinstall just one of them.  The non-new for the GeForce cards and the -new for the newer cards.

---

