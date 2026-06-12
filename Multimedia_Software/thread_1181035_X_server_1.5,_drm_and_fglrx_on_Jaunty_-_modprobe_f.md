---
title: "X server 1.5, drm and fglrx on Jaunty - modprobe fails"
date: 2009-06-07
forum: Multimedia Software
---

### Post by zak on 2009-06-07
I had the misfortune of believing that ATI would provide up to date driver support for more than a year or so after production, so I'm stuck with a laptop with a mobile FireGL and no current drivers.

I'm trying to run an [older X server](http://ubuntuforums.org/showthread.php?p=7416210) compiled with apt-build from the Intrepid sources on Jaunty. There were a few rough spots getting that working, but it's working now and I have X.org server 1.5.2 running with fglrx, but no 3D acceleration or direct rendering. I cannot load the fglrx kernel module and the drm module at the same time.

```

$ sudo modprobe drm
$ sudo modprobe fglrx
FATAL: Error inserting fglrx (/lib/modules/2.6.28-11-generic/updates/dkms/fglrx.ko): Operation not permitted

```
```

$ sudo modprobe fglrx
$ sudo modprobe drm
FATAL: Error inserting drm (/lib/modules/2.6.28-11-generic/kernel/drivers/gpu/drm/drm.ko): Cannot allocate memory

```

I've tried various different combinations of kernel and Catalyst drivers. To be specific, I'm certain I've tried every possible combination of kernels 2.6.28-11 and 2.6.27-11 with Catalyst 8.12, 9.1 and 9.3.

There's also a firepro_8.583 package that claims to be for my FireGL v5200, but displays an "unsupported hardware" icon on the screen when I try to use it. I assume it's for the desktop version of this card. It works for non-accelerated video as well.

Edit: now I see that dri and fglrx aren't intended to be loaded at the same time. My problem was that /dev/dri/card0 did not exist.

---

### Post by ssri on 2009-06-23
Funny, I just apt-get installed 2.6.28-11 from jaunty's repos on my kubuntu intrepid install.  So long as I installed the headers, the kernel and its source, fglrx and virtualbox automatically set up their dkms settings.  So, I can enjoy features from the new kernel and keep catalyst 9.3 running!

---

