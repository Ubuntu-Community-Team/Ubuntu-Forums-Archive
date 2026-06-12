---
title: "Wireless Not Always Up / 64 bit &amp; Atheros"
date: 2009-01-10
forum: Networking &amp; Wireless
---

### Post by cd-r80 on 2009-01-10
Hi! My wireless connection does not work on every boot, more like randomly.

I Have:
lspci
Atheros Communications Inc. AR242x 802.11abg
Under laptop:AR5BxB63

Wicd
WLAN-AP shows always 50% or more.

Ndiswrapper-1.53
Older ndiswrapper removed.

Driver
ar5007eg-64-0.2 

Blacklisted ok

Where i could have a problem?

---

### Post by cd-r80 on 2009-01-10
I have also:
 ndiswrapper -l
net5211 : driver installed
	device (168C:001C) present (alternate driver: ath_pci)
But I cannot find any ath_pci? Conflict?

depmod -n | grep alias | grep -v ':' | grep -i ath_pci
shows nothing.

---

