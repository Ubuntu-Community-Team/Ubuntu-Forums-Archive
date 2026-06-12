---
title: "Atheros AR242x - Hardware error"
date: 2009-01-29
forum: Networking &amp; Wireless
---

### Post by endotoxin on 2009-01-29
I've been tracking some problems with an Atheros mini_pci card in my Compaq Presario C751NR:

lspci:
dave@dave-laptop:~$ lspci|grep Ath
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
dave@dave-laptop:~$ 

/var/log/syslog:
Jan 29 17:01:31 dave-laptop kernel: [  247.310114] ath5k phy0: gain calibration timeout (2427MHz)
Jan 29 17:01:31 dave-laptop kernel: [  247.310121] ath5k phy0: can't reset hardware (-11)

===

I've discovered this problem usually occurs at start up. Only a complete power cycle will solve this problem, and only 50% of the time at that.

Currently running compat-wireless-2009-01-25 from [http://wireless.kernel.org/download/compat-wireless-2.6/](http://wireless.kernel.org/download/compat-wireless-2.6/) . Unloading and reloading the ath5k module does not solve this problem. Possible fix mentioned in [http://article.gmane.org/gmane.linux.kernel.wireless.general/24307/match=ath5k+phy0+can%27t+reset+hardware+11](http://article.gmane.org/gmane.linux.kernel.wireless.general/24307/match=ath5k+phy0+can%27t+reset+hardware+11) which points at a patch at [http://www.spinics.net/lists/linux-wireless/msg23404.html](http://www.spinics.net/lists/linux-wireless/msg23404.html)

Has anyone else encountered this problem?

---

