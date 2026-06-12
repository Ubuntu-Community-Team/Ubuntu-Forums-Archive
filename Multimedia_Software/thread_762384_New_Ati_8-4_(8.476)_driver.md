---
title: "New Ati 8-4 (8.476) driver"
date: 2008-04-22
forum: Multimedia Software
---

### Post by Evzen on 2008-04-22
Hello!

Does anybody manage to successfully install the newest ati 8-4 driver (version 8.476) on Hardy Heron?. It is recently available on the ATI/AMD official pages. I went step-by-step along this guide [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide"). However, I was able to get only two results:

1) Functional driver, version 8.473 (no idea how, because my system contains only 8.476 packages)
2) When I have purged of everything, that contains fglrx or 8.473 in the name before the installation, I end up with nonfunctional 3D (driver was set to mesa)

Does anybody succeeded to run 8.476?

---

### Post by terry1311 on 2008-04-25
I have the same problem. I upgraded my Laptop and Desktop (both with ATI cards) from 7.10 to 08.04 and they both reverted to mesa. I tried installing the latest driver from ATI, and the same happened. 

Still looking to resolve it...

---

### Post by jshbbe on 2008-04-25
I'm having the same problem.  I try installing it, but then when I restart and run the ati control center it says that the driver isn't installed.  When I run fglrxinfo it also says that it is still set to Mesa.

---

### Post by Lemony Fresh on 2008-04-26
I am having the same trouble.  ATI X800

---

### Post by buttonpusher7 on 2008-04-26
Hello. Same problem here. When I did the 8.04 upgrade the fglrx driver worked fine. I noticed the screensaver was very slow about 8hours after install. After a fglrxinfo. it showed the mesa driver. When I ran dpkg-reconfigue xserver-xorg. no monitor or video info was listed.

---

### Post by SandmanXC on 2008-04-26
I have the same problem with ATI Xpress 200M. Everything runs slow as hell, and i have Mesa, too.

---

