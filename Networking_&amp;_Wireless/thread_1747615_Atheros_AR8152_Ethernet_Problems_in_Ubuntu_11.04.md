---
title: "Atheros AR8152 Ethernet Problems in Ubuntu 11.04"
date: 2011-05-02
forum: Networking &amp; Wireless
---

### Post by phoenix910 on 2011-05-02
Hi all, I realise there are a few threads of issues with the AR8152 chipset and Ubuntu 11.04, however, my issue does not appear to be the same as others, nor does there appear to be a consistent solution yet. My ethernet worked fine in Ubuntu 10.10, but after upgrading to 11.04, I experience the errors I am about to explain. I also experience these when booting off a Ubuntu 11.04 Live CD, so it's not just the upgrade the caused the issues. The issue is, if I turn on my system without the ethernet cable plugged in, and then plug the ethernet cable in once I've logged into Ubuntu, the system will not detect it, at all. No amount of network manager of dhclient eth0 will get it to function, however, the device itself still appears in the system.

If I turn the system on with the ethernet plugged in, however, it will get an IP address and function correctly. I tried to download the drivers from Atheros and build them, but for whatever reason it complained about me not having autoconf.h or automake.h (can't remember which), despite having build-essentials and linux-headers-generic installed. Anybody have any suggestions? This ethernet device is on an Aspire One D255. Thanks

---

### Post by phoenix910 on 2011-05-02
UPDATE: I patched the Atheros driver with this patch:
[http://ubuntuforums.org/showpost.php?p=10405440&postcount=1](http://ubuntuforums.org/showpost.php?p=10405440&postcount=1)
Which allowed me to build and install the kernel module, but this still didn't fix the issue. Neither did changing the NetworkManager.conf option for "managed" to true.

---

