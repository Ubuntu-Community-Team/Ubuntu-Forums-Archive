---
title: "'Kernel Panic' with Belkin Wireless PCMCIA"
date: 2005-12-13
forum: Networking &amp; Wireless
---

### Post by ukch on 2005-12-13
Hi,

I have recently bought a Belkin 802.11g PCMCIA wireless card, which apparently has the RT2500 chipset, after reading on the Wiki that this chipset is fully supported in Breezy. I have completely upgraded my system to Breezy yesterday, but I found that the system would hang on boot up with the wireless card inserted. Also, inserting the wireless card while the system was running would also freeze the entire system.

I tried booting up in single-user mode, and I got the following message while the system was booting:

```
CPU0: Machine Check Exception: 0000000000000007
Bank 3: b400000000000833 at 000000001c 40000c
Kernel panic - not syncing: Unable to continue
```

I am running kernel 2.6.12-10-k7 with the rt2500 module that comes with the kernel. The model number of my card is F5D7010 version 3000uk.

Could this be a hardware fault? The card works fine in Windows.

---

