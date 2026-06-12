---
title: "Wireless Not Working"
date: 2013-04-28
forum: Networking &amp; Wireless
---

### Post by Silvericy on 2013-04-28
Hello! i just messed up my lubuntu, i ran the 13.04 update and the wireless suddenly stopped working........ i have already had to fix this with previous updates, i have a dell E6400, i have already ran the _lspci -nn | grep 0280_ command, and this is what it told me _0c:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)_

any help?:confused:

---

### Post by praseodym on 2013-04-28
Hi,

please show
```

iwconfig
lsmod
rfkill list
cat /etc/resolv.conf
route -n
dmesg | egrep 'wl|b43'
```

---

### Post by dandroid13 on 2013-04-28
It seems that the Broadcom proprietary driver is broken for everyone with Raring. I fixed mine by installing bcmwl-kernel-source from Quantal.

---

### Post by jmn2k1 on 2013-04-28
> **dandroid13 said:**
> It seems that the Broadcom proprietary driver is broken for everyone with Raring. I fixed mine by installing bcmwl-kernel-source from Quantal.

Confirming that installing the quantal version of the driver ([http://packages.ubuntu.com/quantal/bcmwl-kernel-source](http://packages.ubuntu.com/quantal/bcmwl-kernel-source)) is working for the BCM4313.

---

