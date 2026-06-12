---
title: "Wifi driver affecting boot process"
date: 2012-11-14
forum: Networking &amp; Wireless
---

### Post by norm.h on 2012-11-14
Reference 2 threads:
Boot problem - Wireless & Networking, and Ubuntu 12.04 Wifi Drivers - Hardware (from Post 54)

I have done another clean install, and all works OK until I install the compat-wireless driver.
After that, although I can connect wirelessly, I get the boot problem described in the thread referenced above.
It would seem that the installation of this driver is affecting something.

The last few lines of the "make install" process, although not referred to in the instructions, refer to unloading / loading. modules, which I ignored.

Could this be relevant?

---

### Post by norm.h on 2012-11-15
On advice from elsewhere, I installed the 3.6.6 kernel.
Then I found and installed the the compat-wireless 3.6.6-1 driver from linux wireless.org.
I've done a full reboot and couple of restarts and all is well.

---

