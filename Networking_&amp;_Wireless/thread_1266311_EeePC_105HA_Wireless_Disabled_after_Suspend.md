---
title: "EeePC 105HA Wireless Disabled after Suspend"
date: 2009-09-14
forum: Networking &amp; Wireless
---

### Post by Tortel on 2009-09-14
I have a problem with my EeePC 1005ha, whenever I suspend or hibernate my system, the wireless becomes disabled. If I use the buttons to toggle the wireless off/on, it will work for a second and start to connect then go back to disabled.

Wireless info (From lspci):
```
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
```

Kernel Version:
```
2.6.29-1-netbook i686
```

I have the linux backports installed, version 2.6.28.15.20 - using the ath9k driver.

Ive tried several fixes so far, and none have worked.
Fixes Ive tried:
[Editing /etc/default/acpi-support](http://lilserenity.wordpress.com/2007/10/31/fix-ubuntu-dropping-wireless-on-suspendhibernate-resume/)
[Editing /etc/NetworkManager/nm-system-settings.conf](http://art.ubuntuforums.org/showpost.php?p=7443864&postcount=8)
 Ive also tried several others that I forgot about, and I also built the driver from source too.

Ideas? Need more output? Just ask me.

---

### Post by Tortel on 2009-09-14
Found a fix. I still have the edit in /etc/default/acpi-support where I changed STOP_SERVICES="" to STOP_SERVICES="networking" and I also installed Wicd from the advice in [_this_](http://ubuntuforums.org/showpost.php?p=7717353&postcount=30) post. Not too sure why that was happening, but its all better now.

---

### Post by sneakerbg_e on 2011-01-07
Thanks :) It's the only thing that works for my 1005ha. Wicd rocks

---

