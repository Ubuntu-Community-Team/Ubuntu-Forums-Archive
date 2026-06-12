---
title: "agpgart, linux kernels 6.12+ &amp; Asus K8V-X SE"
date: 2005-12-31
forum: Multimedia &amp; Video
---

### Post by Amon_Re on 2005-12-31
Just a bug report really, it seems that current linux kernels are unable to properly activate/detect the AGPGART inside the amd64 CPU when used in conjunction with this ASUS motherboard.

This bug has been forwarded to the LKML, and has been discussed on the gentoo forums.

The amd64-agp module incorrectly recognises the aperture size specified in the bios, trying to use the 3D accellerated drivers for ati cause hangs. testgart.c also fails.

More info can be provided if needed.
If someone has had simular problems (and managed to solve them ;)) please do post them.

---

### Post by Amon_Re on 2006-01-01
After some more digging, it seems the problem might actually be mtrr related, turns out that mtrr is unable to read my BIOS properly, will post again when i find the cause or a work-arround

---

### Post by Amon_Re on 2006-01-02
Just to conform that this system also has problems with DRI when using a R128 & the kernel's own drivers etc. When using DRI the machine crawls to a slow death, disabling DRI makes it fly.

Anyone who knows how to solve this one?

---

