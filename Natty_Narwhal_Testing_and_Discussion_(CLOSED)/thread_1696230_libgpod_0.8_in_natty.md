---
title: "libgpod 0.8 in natty ?"
date: 2011-02-27
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by lucasart on 2011-02-27
Will libgpod 0.8 finally be included as default in Natty ?

I saw on libgpod webnsite, that 0.8.0 is now declared as a stable release, so there's no reason not to include it in Ubuntu 11.04's repositries by default.

This is very important, as it finally resolves the everlasting problem of compatibility with Ipod Nano 5g, and many other Apple devices (iphone ipod touch etc.)

---

### Post by xgt001 on 2011-02-27
libgpod4 0.7.95 is included in alpha 2 ... by the final release most likely 0.8 will be inlcuded

---

### Post by lucasart on 2011-02-27
> **xgt001 said:**
> libgpod4 0.7.95 is included in alpha 2 ... by the final release most likely 0.8 will be inlcuded

Let's hope so, but in Debian sid, they still have 0.7.95, so if they just to a debian import and don't look at this problem specifically, they'll probably not do it.

---

### Post by MadCow108 on 2011-02-27
if it introduces new features you have to request a freeze exception and motivate why it should be added after feature freeze (+ test for regressions).
As debian is still on 7.95 you either have to package the new version yourself or ask the debian maintainers to do so very soon.
[https://wiki.ubuntu.com/FreezeExceptionProcess](https://wiki.ubuntu.com/FreezeExceptionProcess)

if it is a bug fix only release the chances of getting it in natty are higher.

---

### Post by lucasart on 2011-03-06
> **MadCow108 said:**
> if it introduces new features you have to request a freeze exception and motivate why it should be added after feature freeze (+ test for regressions).
As debian is still on 7.95 you either have to package the new version yourself or ask the debian maintainers to do so very soon.
[https://wiki.ubuntu.com/FreezeExceptionProcess](https://wiki.ubuntu.com/FreezeExceptionProcess)

if it is a bug fix only release the chances of getting it in natty are higher.

Thanks, but that seems way to complicated for me. What I have however is a debian package for libgpod 0.8, but can't install it because it says it is conflicting with libgpod 0.7.xyz installed with Ubuntu. Do you know how to just replace the pold package with the new one ?

---

### Post by MadCow108 on 2011-03-06
try removing the old one before installing the new one.

---

