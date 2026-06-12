---
title: "RT2500 AMD64 Module problem - stock and compiled kernels"
date: 2005-03-23
forum: Networking &amp; Wireless
---

### Post by narb on 2005-03-23
I have had this module working in Mandrake with the mandrake stock kernel and with compiled kernels. After ditching Mandrake and moved to AMD64 Kubuntu the driver module rt2500 will not register the interface with the kernel. It should be addressed as ra0.

The module appears to compile cleanly and is installed in the correct /lib/modules/ tree. modprobe rt2500 doesn't give any errors and dmesg shows that the same PCI IRQ is getting assigned that is in lspci -v. 

/etc/modprobe.d/rt2500 contains:
alias ra0 rt2500

when trying to bring up the interface:
root@narghoul:/home/narb # ifconfig ra0 up
ra0: ERROR while getting interface flags: No such device

I have tried loading the kernels with PCI=routeirq with the same results.
On a Sager 4750, AMD 64 3700+
Anyone have any ideas?

---

