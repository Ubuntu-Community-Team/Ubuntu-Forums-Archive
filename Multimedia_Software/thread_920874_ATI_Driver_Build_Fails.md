---
title: "ATI Driver Build Fails"
date: 2008-09-15
forum: Multimedia Software
---

### Post by solarwind on 2008-09-15
Hey all, I have built and installed a custom kernel for Ubuntu (from kernel.org). I have an ATI mobility X300 card and have generated the Ubuntu/hardy deb files using the ati binary installer (just as the wiki says).

However when installing the debs, I get this:

```
Error!  Build of fglrx.ko failed for: 2.6.26.5 (i686)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.522/build/ for more information.

Error! Could not locate fglrx.ko for module fglrx in the DKMS tree.
You must run a dkms build for kernel 2.6.26.5 (i686) first.

```

How do I fix this error? I really need the binary drivers with my custom kernel.

---

### Post by solarwind on 2008-09-20
Bump.

---

### Post by khelben1979 on 2008-09-20
Maybe you should try with an older kernel version?

---

### Post by solarwind on 2008-09-20
> **khelben1979 said:**
> Maybe you should try with an older kernel version?

It's not the kernel. I upgraded kernels because I had to. There was a bug in the older one (the one that comes with Ubuntu).

---

