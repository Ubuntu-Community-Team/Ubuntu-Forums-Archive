---
title: "problem with virtualbox 3.1.6 networking"
date: 2010-07-31
forum: Networking &amp; Wireless
---

### Post by didix_1 on 2010-07-31
I can't use Virtualbox with network mode : Host-only Adapter because the interface vboxnet0 is not created.
I think this is something related to dkms , and if i go from virtualbox menu to File-> Preferences-> Network and try to ad host-only interface i get the following :
Failed to create the host-only network interface.
 Failed to execute 'VBoxNetAdpCtl add' (exit status: 768).
Once i reinstall all the package of virtualbox the vboxnet0 is there and everything is normal but when i restart my ubuntu 10.04 lucid the problem is present again is there a way to solve this or should i always reinstall the packages of virtualbox to use it??!
thank you

---

### Post by didix_1 on 2010-08-01
I've noticed also that the usb wasn't detected by doing a little search i find out that installing the vbox from repositories wasn't good so i removed it and download the deb package from the offical website of virtualbox :KS

---

