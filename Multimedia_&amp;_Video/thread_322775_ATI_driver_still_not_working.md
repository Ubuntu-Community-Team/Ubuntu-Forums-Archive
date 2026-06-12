---
title: "ATI driver still not working"
date: 2006-12-21
forum: Multimedia &amp; Video
---

### Post by circ on 2006-12-21
ive tried just about every method mentioned on the forums, most of them several times. the results werent any different with breezy either. anyhow, this time i grabbed the installer from ati's site and compiled it with the method mentioned at

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

not surprisingly, it didnt work this time either. it is however an ubuntu issue, as i get 3d acceleration working just fine with kanotix and fedora core 6. altho fc6 used the mesa drivers, it wasn't the usual 2d ones and the fps with glxgears was good.

dmesg | grep fglrx
[17179586.368000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179586.368000] [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
[17179586.368000] [fglrx] module loaded - fglrx 8.28.8 [Aug 17 2006] on minor 0
[17179590.192000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[17179590.192000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[17179590.192000] [fglrx] AGP detected, AgpState   = 0x1f004e0b (hardware caps of chipset)
[17179590.192000] [fglrx:firegl_unlock] *ERROR* Process 3588 using kernel context 0
[17179892.400000] [fglrx] Internal AGP is not supported in 2.6 kernel.
[17179892.400000] [fglrx:firegl_unlock] *ERROR* Process 4018 using kernel context 0

so its down to some conflict with AGP? i have no idea what that means. anyway, onto xorg.0.log, heres a snippet -

(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

that shows up even though ive disabled composite in xorg.conf. i tried 'Disable', 'false' and '0' and it didnt make any difference.

---

