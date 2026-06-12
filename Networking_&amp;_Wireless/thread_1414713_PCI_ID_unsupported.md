---
title: "PCI ID unsupported"
date: 2010-02-23
forum: Networking &amp; Wireless
---

### Post by bullu on 2010-02-23
I tried the following:

```

mezry@abizit-laptop:~$ lspci -nn | grep 14e4
02:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)

```It looks like that my PCI ID 14e4:432b is unsupported which i found out frm [http://wireless.kernel.org/en/users/Drivers/b43#Known_PCI_devices](http://wireless.kernel.org/en/users/Drivers/b43#Known_PCI_devices)


What does this mean??

---

### Post by chili555 on 2010-02-24
It means exactly what it says; the b43 module is not correct for your device. Is there anything listed in System -> Administration -> Hardware Drivers?

Your card is supported in the driver *wl*:```
$ modinfo wl | grep 432B
alias:          pci:v0000[COLOR="Blue"]14E4[/COLOR]d0000[COLOR="Blue"]432B[/COLOR]sv*sd*bc*sc*i*
```Let's just figure out the quick and easy way to get it.

---

