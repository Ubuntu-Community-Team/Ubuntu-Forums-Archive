---
title: "ATi Radeon 9600... what am I doing wrong here?"
date: 2006-09-10
forum: Multimedia &amp; Video
---

### Post by Mazza558 on 2006-09-10
Please note: On my GRUB display, it lists 2 copies of Ubuntu, is this the problem?

Basically, I followed the exact steps [HERE]("http://ubuntuforums.org/showthread.php?t=204910") with the latest Radeon Driver. I also blacklisted fglrx before and un-blacklisted it afterwards. Basically,

This is what it says in the xorg log:



```
[drm] failed to load kernel module "fglrx" (WW) fglrx(0): Failed to open DRM connection (--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM (II) fglrx(0): AGP card detected (WW) fglrx(0): board is an unknown third party board, chipset is supported
```


and then further down:

```

(II) fglrx(0): driver needs X.org 6.8.x.y with x.y >= 99.8 (II) fglrx(0): detected X.org 7.0.0.0 (II) Loading extension ATIFGLRXDRI (II) fglrx(0): doing DRIScreenInit drmOpenDevice: node name is /dev/dri/card0 drmOpenDevice: open result is -1, (No such device or address) drmOpenDevice: open result is -1, (No such device or address) drmOpenDevice: Open failed drmOpenDevice: node name is /dev/dri/card0 drmOpenDevice: open result is -1, (No such device or address) drmOpenDevice: open result is -1, (No such device or address) drmOpenDevice: Open failed [drm] failed to load kernel module "fglrx" (II) fglrx(0): [drm] drmOpen failed (EE) fglrx(0): DRIScreenInit failed! (WW) fglrx(0): *********************************************** (WW) fglrx(0): * DRI initialization failed! * (WW) fglrx(0): * (maybe driver kernel module missing or bad) * (WW) fglrx(0): * 2D acceleraton available (MMIO) * (WW) fglrx(0): * no 3D acceleration available * (WW) fglrx(0): ********************************************* *
```

In addition, fglrxinfo shows the infamous Mesa drivers. What am I doing wrong?

EDIT: Apologies for the way the CODE tags turned out

---

### Post by Mazza558 on 2006-09-11
Bumpage... 

Anyone have any ideas?

---

### Post by sirclaudio on 2006-09-11
Can you describe your system? I also have an ATI and can't get DRI due to agp drivers. In a gentoo forum, i've read that in some AMD64 systems, the K8 IOMMU support must be disabled.
So i decided install linux again and try , later i'll post the results.

---

### Post by Mazza558 on 2006-09-11
My CPU is AMD Athlon 64, but I'm using th 32 bit Ubuntu for my wireless to work. I have 1GB of RAM, etc, is there anything else you need to know?

---

### Post by Mazza558 on 2006-09-12
Anyone else have any ideas?

---

### Post by silvy on 2006-09-12
Please check the modules.dep file with an editor (look at /lib/modules/2.6.15-26-686 whereas "2.6.15-26-686" should be change with your current kernel number).
There should be 1 entry only with fglrx (e.g. /lib/modules/2.6.15-26-686/kernel/drivers/char/drm/fglrx.ko: /lib/modules/2.6.15-26-686/kernel/drivers/char/agp/agpgart.ko)

---

### Post by Mazza558 on 2006-09-13
In that file there's no sign of a fglrx anywhere. I navigated to the drm folder and there's only "radeon" but no "fglrx".

---

