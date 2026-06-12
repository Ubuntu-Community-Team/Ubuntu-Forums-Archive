---
title: "Wake On LAN stopped working after kernel upgrade to 3.2.0-30"
date: 2012-09-12
forum: Networking &amp; Wireless
---

### Post by denrix on 2012-09-12
Hi,

I'm running Lubuntu 12.04 on my home server. Last Friday I've been offered a host of updates, including getting a new kernel 3.2.0-30, after which my WOL functionality has gone.

Admittedly, it worked only from the S5 (shutdown) state, I never managed to make it work for the S3 state.

Could anybody to give me some idea, how I would be able to fix the problem?

Here are some info:

_lspci_
```
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
```

_ethtool eth0_
```
Supports Wake-on: pumbg
	Wake-on: g
```

_/proc/acpi/wakeup_
```
PCI0	  S5	*enabled   no-bus:pci0000:00
LAN0	  S5	*enabled   pci:0000:00:12.0
```

_/etc/init.d/halt_
```
NETDOWN=no
```

I would really appreciate any help.

---

### Post by denrix on 2012-09-13
I've downloaded and installed 3.4 kernel, but it didn't help :(

---

