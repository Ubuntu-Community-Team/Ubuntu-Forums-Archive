---
title: "Intel 536EP Problems"
date: 2005-12-14
forum: Networking &amp; Wireless
---

### Post by kingfish on 2005-12-14
The modem was working great but then I did a wipe and went with Ubuntu 5.10 (Had 4.10). And for what ever reason I cannot get it to compile the drivers and install.

I am following this guide on how to install it:
[https://wiki.ubuntu.com//IntelFiveThreeSixEPModemHowto/](https://wiki.ubuntu.com//IntelFiveThreeSixEPModemHowto/)

Here is where I get stuck with it:

david@ubuntu:~/Intel-536$ make 536
Try `uname --help' for more information.
Module precompile check
Current running kernel is: 2.6.12-10-686
/lib/modules... autoconf.h does not exist
please install kernel source
make: *** [check] Error 1
david@ubuntu:~/Intel-536$

---

### Post by coder928 on 2005-12-17
try installing the kernel headers

type

sudo apt-get install linux-headers-$(uname -r)

and then try installing the driver again, hope this helps

---

### Post by coder928 on 2005-12-17
also the defult linux drivers for the modem are for the 2.4.x series of kernels, so you may need to source new drivers that support 2.6.x, well my modem was shiped with drivers that were only 4 2.4.x

---

