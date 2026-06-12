---
title: "ndiswrapper, windows hardware drivers, 10.10"
date: 2011-03-05
forum: Networking &amp; Wireless
---

### Post by capemayal on 2011-03-05
I really want to drop Windows, but wireless connectivity and frequent crashes are really discouraging me.
 
I have a dual-boot W XP with Ubuntu 10.10.
 
Exuse me, as I do not have the computer on, so I'm writing this from my weak memory :P

[LIST=1]
[*]USB Adapter - Netgear WNDA3100-100NAS = v2
[*]The adapter works under W XP with no problems
[*]The router, Linksys WRT54G sees the adapter in the dhcp table
[*]lsusb lists the adapter.
[*]I have copied the drivers from the install CD onto the desktop.
[*]I cannot figure out how to install or access those drivers for the installation.
[*]I tried to install the ndiswrapper from the software center, but the center shows it's available from the "main" source. I've looked in the package manager, but can't find it. When I go into terminal, and enter one of the suggested commands in the forums, it can't be located.
[*]I have a Belkin F5D8010 installed on this computer, and it works great under W XP.
[*]I want to try to get this installed, but until I can figure out installation of the ndiswrapper and how to access it, and get the drivers recognized, I'm at a standstill.
[/LIST]Any help would be greatly appreciated.
 
Thanks,
Al

---

### Post by Old_Grey_Wolf on 2011-03-05
In the Ubuntu Software Center search for "Windows Wireless Drivers". Install it. "Windows Wireless Drivers" is a graphical front end for ndiswrapper. It will install ndiswrapper for you when it installs.

You can use it to install the drivers from the CD.

---

