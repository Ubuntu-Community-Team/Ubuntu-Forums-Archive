---
title: "fglrx module not found"
date: 2008-03-01
forum: Multimedia &amp; Video
---

### Post by marioquark on 2008-03-01
hi,
i have a ati radeon x1600 card, and after the envy script  installation i got this messages in Xorg.log file:
```

drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(WW) fglrx(0): Failed to open DRM connection

...

(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized.
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
```

---

### Post by marioquark on 2008-03-01
i tried also to compile it with module assistant, but i get this:

```
sudo module-assistant build fglrx
...

FATAL: modpost: GPL-incompatible module fglrx.ko uses GPL-only symbol
```

---

### Post by marioquark on 2008-03-01
note that i have a realtime kernel:

```
Linux LASER 2.6.21-1-multimedia-486 #1 SMP PREEMPT RT Fri Jun 22 19:13:23 UTC 2007 i686 GNU/Linux
```

---

