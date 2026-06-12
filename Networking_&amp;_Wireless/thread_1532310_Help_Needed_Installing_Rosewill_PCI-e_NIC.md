---
title: "Help Needed Installing Rosewill PCI-e NIC"
date: 2010-07-16
forum: Networking &amp; Wireless
---

### Post by jMon54 on 2010-07-16
My onboard NIC has been flaky so I decided to install a Rosewill PCI-e NIC (RC411) but cannot get it to work though it lights green.  I ran the install per the readme and got this:

Check old driver and unload it.
rmmod r8168
Build the module and install
/home/jmon/rosewill-nic/r8168-8.018.00/src/r8168_n.c: In function ‘rtl_get_eeprom’:
/home/jmon/rosewill-nic/r8168-8.018.00/src/r8168_n.c:1794: warning: ‘ret’ may be used uninitialized in this function
[: 48: r8168: unexpected operator
Depending module. Please wait.
load module r8168
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
Completed.

And then per the instructions I ran lsmod | grep r8168 and I got this:
r8168                  91277  0

When I run ifconfig -a it does not show up.

Any help in getting this NIC to work would be much appreciated. TIA

---

