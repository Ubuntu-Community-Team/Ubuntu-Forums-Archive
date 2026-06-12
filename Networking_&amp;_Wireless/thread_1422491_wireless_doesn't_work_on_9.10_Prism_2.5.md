---
title: "wireless doesn't work on 9.10 Prism 2.5"
date: 2010-03-05
forum: Networking &amp; Wireless
---

### Post by pullmandave on 2010-03-05
I'm running an IBM A30p laptop with the Prism 2.5 wireless builtin. I've just upgraded the kernel to version 2.6.31-20-generic. I also use wicd as my network manager. I've tried the orinoco drivers, can't connect to anything and after a bit the device goes away (no longer listed in the ifconfig, still in the iwconfig as eth1). So, I unloaded these modules and gave the hostap drivers a go. When I load the hostap_pci module the system hangs. On the console (I'm not using the window interface) I see CPU hung messages. This has never worked on the 9.10 version. It was working on version 8.04 LTS.

---

