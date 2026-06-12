---
title: "How to upgrade i810 video driver"
date: 2006-07-11
forum: Multimedia &amp; Video
---

### Post by Focher on 2006-07-11
Hi,

I would like to use an updated version of the i810 video driver. I have a binary version of the 1.6.0 version of the i810 driver and it is specifically compiled to support X.org 7.0. However, when I try to replace the existing /usr/lib/xorg/modules/drivers/i810_drv.so file and start the X server, I get the following in the /var/log/Xorg.0.log file:

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.12 i686
[extraneous stuff cut]
(II) LoadModule: "i810"
(II) Loading /usr/lib/xorg/modules/drivers/i810_drv.so
(II) Module i810: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.6.0
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 1.0
(EE) module ABI major version (1) doesn't match the server's version (0)
(II) UnloadModule: "i810"
(II) Unloading /usr/lib/xorg/modules/drivers/i810_drv.so
(EE) Failed to load module "i810" (module requirement mismatch, 0)

Is there a way to tell X to ignore the ABI major version?

Thanks.

---

