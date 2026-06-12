---
title: "Intel integrated graphics driver problem"
date: 2019-04-25
forum: Multimedia Software
---

### Post by funkymonk96 on 2019-04-25
I have a dual booted XPS 13 (9380) running ubuntu 18, and troubleshooting wifi problems I came across a video drivers problem. Running a hardware probe shows that the the i915 driver is not properly installed, and the system, instead of loading the modeset/i915 driver loads the FBDEV one (which I'm told is not a good one). 

link to the log file:
[https://linux-hardware.org/index.php?probe=5b5057a51d&log=xorg.log](https://linux-hardware.org/index.php?probe=5b5057a51d&log=xorg.log)

trying a live usb install of ubuntu and running the same probe (both on ubuntu 18 and 19) does not show any issues with this driver
log for ubuntu 18:
[https://pastebin.com/QuC7yudu](https://pastebin.com/QuC7yudu)
log for ubuntu 19:
[https://pastebin.com/UU4YyJzN](https://pastebin.com/UU4YyJzN)

Does anybody have a fix or a way to reinstall the correct drivers (hopefully without a clean install of ubuntu)?

---

### Post by TheFu on 2019-04-25
Run this:
```
dpkg -l|grep intel|grep xserver
```
to get the name of the package, then just reinstall it.

Something like:
```
sudo apt-get --reinstall install xserver-xorg-video-intel
```
there might be an ubuntu release number in your package.

Mine has this name: xserver-xorg-video-intel-hwe-16.04 because I'm running 16.04 with the HWE kernel.

---

### Post by Yellow Pasque on 2019-04-26
```
BOOT_IMAGE=/boot/vmlinuz-4.13.0-041300-generic
```

You're booting into an old kernel. Ubuntu 18.04.1 used 4.15.x

---

### Post by funkymonk96 on 2019-04-26
tried it but didn't fix it, problem might be the kernel, as mentioned, however I have removed kernel 4.13 and now running either 5 or 5.0.7 the trackpad and keyboard are completely unresponsive. Unfortunately those are the only two kernels I have installed, is there a way to install a new kernel from the grub menu or from recovery mode? Or is a fresh install my only option left?

---

### Post by TheFu on 2019-04-26
You could restore from the backups you have.

---

### Post by funkymonk96 on 2019-04-27
Fixed by fresh reinstall, driver error is gone too

---

