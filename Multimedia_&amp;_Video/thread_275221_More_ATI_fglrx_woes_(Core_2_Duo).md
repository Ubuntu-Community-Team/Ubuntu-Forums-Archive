---
title: "More ATI fglrx woes (Core 2 Duo)"
date: 2006-10-11
forum: Multimedia &amp; Video
---

### Post by ice9mike on 2006-10-11
Please help. I have read and read and tried and tried, but I am unable to get ati xorg drivers (8.29.06) working on my Core 2 Duo machine. I am using the amd64 distribution. Any help is appreciated. Here are my files. As you can see DRI does not initialize. My video card is a Visiontek X1300. Thanks in advance.

---

### Post by ice9mike on 2006-10-11
Sorry, here are the warnings

II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0x2aaaadfc9000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x10000000
(II) fglrx(0): FBMM initialized for area (0,0)-(1728,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1728,1050) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(**) fglrx(0): DPMS enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used

---

