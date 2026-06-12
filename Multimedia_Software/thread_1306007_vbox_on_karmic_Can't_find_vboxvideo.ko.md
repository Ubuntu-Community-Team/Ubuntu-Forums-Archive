---
title: "vbox on karmic: Can't find vboxvideo.ko"
date: 2009-10-30
forum: Multimedia Software
---

### Post by eantoranz on 2009-10-30
Hi!

I have kubuntu running on virtual box. After I dist-upgraded to karmic, X can't find vboxvideo.ko module (though it's on the system):

```

locate vboxvideo.ko
/lib/modules/2.6.31-14-generic/updates/dkms/vboxvideo.ko
/var/lib/dkms/virtualbox-ose-guest/3.0.8/2.6.28-16-generic/i686/module/vboxvideo.ko
/var/lib/dkms/virtualbox-ose-guest/3.0.8/2.6.31-14-generic/i686/module/vboxvideo.ko
/var/lib/dkms/virtualbox-ose-guest/3.0.8/build/vboxvideo_drm/.vboxvideo.ko.cmd
/var/lib/dkms/virtualbox-ose-guest/3.0.8/build/vboxvideo_drm/vboxvideo.ko

```

Any ideas what I'm missing?

```

(II) LoadModule: "vboxvideo"
(WW) Warning, couldn't open module vboxvideo
(II) UnloadModule: "vboxvideo"
(EE) Failed to load module "vboxvideo" (module does not exist, 0)
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
        compiled for 1.6.3, module version = 2.2.1
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 0.4.0
        ABI class: X.Org Video Driver, version 5.0
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00@00:02:0

```

---

