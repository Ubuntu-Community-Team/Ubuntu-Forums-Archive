---
title: "ALSA configuration with kernel v. 2.6.26.2"
date: 2008-08-15
forum: Multimedia Software
---

### Post by Buster222 on 2008-08-15
In order to update the alsa driver to v. 1.0.17 (it is required for M-Audio Delta 66 rev E) on Ubuntu 8.04 I compiled and installed kernel version 2.6.26.2 by followed the instructions on [http://www.ubuntugeek.com/automatically-compile-and-install-the-latest-kernel-using-kernelcheck-in-ubuntu.html](http://www.ubuntugeek.com/automatically-compile-and-install-the-latest-kernel-using-kernelcheck-in-ubuntu.html). That apparently went well, as after reboot uname -r reports 2.6.26.2. So far, so good. However, in Audacity | Preferences there is now no alsa driver available. I presume I will have to create a link in /lib/modules to the alsa driver, but I am not familiar enough with this to work out the details. Anybody out there that know how to do this?

---

### Post by mocha on 2008-08-15
Why did you install a new kernel to upgrade Alsa?  I think you  will need to install Alsa after the kernel upgrade anyway.

---

### Post by markbuntu on 2008-08-15
Why are you trying to use audacity?

---

### Post by master_kernel on 2008-08-17
You probably didn't enable ALSA in the kernel configuration (xconfig).

---

