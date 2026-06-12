---
title: "Vesa?"
date: 2012-03-22
forum: Multimedia Software
---

### Post by draucia on 2012-03-22
I don't know anything about graphic cards but I have a:

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

On my laptop (intergrated graphics, I think). But I have reallly slow performance in games in ubuntu. In heroes of newerth I can get over 30fps on average but on ubuntu I get around 15. I checked xorg.log and I think it says I'm using vesa. Isn't that what it defaults to if no other driver is found or something? I know in my previous distro I used mesa.

This is the part I found in in:

>   483.659] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   483.659] (II) Module dbe: vendor="X.Org Foundation"
[   483.659] 	compiled for 1.10.4, module version = 1.0.0
[   483.659] 	Module class: X.Org Server Extension
[   483.659] 	ABI class: X.Org Server Extension, version 5.0
[   483.659] (II) Loading extension DOUBLE-BUFFER
[   483.659] (II) LoadModule: "glx"
[   483.659] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   483.659] (II) Module glx: vendor="X.Org Foundation"
[   483.659] 	compiled for 1.10.4, module version = 1.0.0
[   483.659] 	ABI class: X.Org Server Extension, version 5.0
[   483.659] (==) AIGLX enabled
[   483.659] (II) Loading extension GLX
[   483.659] (II) LoadModule: "record"
[   483.660] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   483.660] (II) Module record: vendor="X.Org Foundation"
[   483.660] 	compiled for 1.10.4, module version = 1.13.0
[   483.660] 	Module class: X.Org Server Extension
[   483.660] 	ABI class: X.Org Server Extension, version 5.0
[   483.660] (II) Loading extension RECORD
[   483.660] (II) LoadModule: "dri"
[   483.660] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   483.660] (II) Module dri: vendor="X.Org Foundation"
[   483.660] 	compiled for 1.10.4, module version = 1.0.0
[   483.660] 	ABI class: X.Org Server Extension, version 5.0
[   483.660] (II) Loading extension XFree86-DRI
[   483.660] (II) LoadModule: "dri2"
[   483.660] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   483.661] (II) Module dri2: vendor="X.Org Foundation"
[   483.661] 	compiled for 1.10.4, module version = 1.2.0
[   483.661] 	ABI class: X.Org Server Extension, version 5.0
[   483.661] (II) Loading extension DRI2
[   483.661] (==) Matched intel as autoconfigured driver 0
[   483.661] (==) Matched vesa as autoconfigured driver 1
[   483.661] (==) Matched fbdev as autoconfigured driver 2
[   483.661] (==) Assigned the driver to the xf86ConfigLayout
[   483.661] (II) LoadModule: "intel"
[   483.661] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   483.661] (II) Module intel: vendor="X.Org Foundation"
[   483.661] 	compiled for 1.10.4, module version = 2.15.901
[   483.661] 	Module class: X.Org Video Driver
[   483.661] 	ABI class: X.Org Video Driver, version 10.0
[   483.661] (II) LoadModule: "vesa"
[   483.661] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   483.661] (II) Module vesa: vendor="X.Org Foundation"
[   483.661] 	compiled for 1.10.2, module version = 2.3.0
[   483.661] 	Module class: X.Org Video Driver
[   483.661] 	ABI class: X.Org Video Driver, version 10.0
[   483.662] (II) LoadModule: "fbdev"
[   483.662] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   483.662] (II) Module fbdev: vendor="X.Org Foundation"
[   483.662] 	compiled for 1.10.0, module version = 0.4.2
[   483.662] 	ABI class: X.Org Video Driver, version 10.0
[   483.662] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[   483.662] (II) VESA: driver for VESA chipsets: vesa
[   483.662] (II) FBDEV: driver for framebuffer: fbdev
[   483.662] (++) using VT number 7

[   483.664] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   483.664] (WW) Falling back to old probe method for vesa
[   483.664] (WW) Falling back to old probe method for fbdev
[   483.664] (II) Loading sub module "fbdevhw"
[   483.664] (II) LoadModule: "fbdevhw"
[   483.664] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   483.664] (II) Module fbdevhw: vendor="X.Org Foundation"
[   483.664] 	compiled for 1.10.4, module version = 0.0.2
[   483.664] 	ABI class: X.Org Video Driver, version 10.0
[   483.665] drmOpenDevice: node name is /dev/dri/card0
[   483.665] drmOpenDevice: open result is 9, (OK)
[   483.665] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[   483.665] drmOpenDevice: node name is /dev/dri/card0
[   483.665] drmOpenDevice: open result is 9, (OK)
[   483.665] drmOpenByBusid: drmOpenMinor returns 9
[   483.665] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[   483.665] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32

---

### Post by Yellow Pasque on 2012-03-22
> [ 483.665] (II) intel(0): Creating default Display subsection in Screen section
You're using the correct intel driver (vesa is just loaded for fallback).

You may want to try the xorg-edgers ppa to see if the latest drivers improve performance.

---

### Post by draucia on 2012-03-22
> **Temüjin said:**
> You're using the correct intel driver (vesa is just loaded for fallback).

You may want to try the xorg-edgers ppa to see if the latest drivers improve performance.

I'm new to ubuntu... so I did add-apt-repository ppa:xorg-edgers and did sudo apt-get update, and upgrade. I tried upgrading through the top right button in unity and doing update programs but it says not all updates can be installed and I can do a "partial upgrade". Did I mess up anywhere? :S

---

