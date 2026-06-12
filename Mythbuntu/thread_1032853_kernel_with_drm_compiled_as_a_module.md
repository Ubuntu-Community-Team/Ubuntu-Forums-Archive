---
title: "kernel with drm compiled as a module?"
date: 2009-01-06
forum: Mythbuntu
---

### Post by jape42 on 2009-01-06
Hi All,

I'm currently using the 2.6.24-23-server kernel. Are there any kernels where drm is compiled as a module?  I'd rather avoid compiling a kernel if I can.

Any thoughts appreciated,

jp

---

### Post by superm1 on 2009-01-07
Any of the generic kernels should be:

test@dell-desktop:~$ modinfo drm
filename:       /lib/modules/2.6.27-11-generic/kernel/drivers/gpu/drm/drm.ko
license:        GPL and additional rights
description:    DRM shared core routines
author:         Gareth Hughes, Leif Delgass, José Fonseca, Jon Smirl
srcversion:     76029178EC5FA4B1BFB4E82
depends:        agpgart
vermagic:       2.6.27-11-generic SMP mod_unload modversions 586 
parm:           debug:Enable debug output (int)

---

