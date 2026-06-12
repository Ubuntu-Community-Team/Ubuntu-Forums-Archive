---
title: "Problem with graphics driver"
date: 2012-01-21
forum: Multimedia Software
---

### Post by CrystalMV on 2012-01-21
Hello everyone. I have an ATI Radeon X1300/X1550 Series graphics card. Its fglrx driver is no longer updated, so I use Mesa driver. However, there's a problem: it crashes some programs. One of the crashes is described here: [https://bugs.freedesktop.org/show_bug.cgi?id=38422](https://bugs.freedesktop.org/show_bug.cgi?id=38422) . When I started using Ubuntu, the version was 11.04 and I didn't get this problem. I tried removing the graphics card, so that integrated card would be used. It worked, but I want another solution, so that I wouldn't need to remove the graphics card. I also tried installing another Mesa driver which emulates OpenGL in software and the problem seems to be gone too, but the emulation is very slow. Is it possible to configure the driver to disable some OpenGL features which are slow in software, such as bilinear/trilinear texture filtering? Or maybe there's something I could do to solve the problem with hardware-accelerated driver?

---

### Post by BC59 on 2012-01-21
Normally the latest FGLRX driver is in this repository:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
```
If you don't have the driver already installed

```
sudo apt-get install fglrx
```

If you like to upgrade it

```
sudo apt-get upgrade
```

---

### Post by CrystalMV on 2012-01-21
When I did this, 3D programs didn't work at all and after rebooting, Ubuntu froze when started. It's a good thing I managed to reinstall Mesa drivers.

---

