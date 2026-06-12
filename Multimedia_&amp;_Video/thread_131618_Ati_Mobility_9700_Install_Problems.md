---
title: "Ati Mobility 9700 Install Problems"
date: 2006-02-16
forum: Multimedia &amp; Video
---

### Post by mclough on 2006-02-16
To start i have a dell inspiron 9100 2.8ghz 512mb with a mobility 9700 64mb
when i install it all go fine untill i get to ```
nice@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```
For the life of me i cant find what i'm doing wrong the ati control is in the applications 
menu can some please tell me where to look to fix this i have no idea where to start 
i just switched from windows to linux 5 days ago so im brandnew to this but i want to learn
Thank You

---

### Post by mclough on 2006-02-18
well i have look at the xorg.0.log file and the only error i see is 
```
(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_EBUSY"
(EE) fglrx(0): cannot init AGP
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xe0bf9000 at 0xb7b27000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xf0000000 FBMappedSize: 0x04000000
(WW) fglrx(0): Failed to set up write-combining range (0xf0000000,0x4000000)
```

anyone have any idea how i can fix this?

---

