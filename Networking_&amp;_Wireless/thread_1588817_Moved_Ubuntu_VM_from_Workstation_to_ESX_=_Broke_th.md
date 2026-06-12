---
title: "Moved Ubuntu VM from Workstation to ESX = Broke the Nic!"
date: 2010-10-05
forum: Networking &amp; Wireless
---

### Post by jonc101 on 2010-10-05
Hey guys,

I moved an Ubuntu 10.04 VM from Workstation to ESXi 4.0 and now the network card isn't been picked up, an ifconfig reveals just the localhost. 

How can I resolve this?

---

### Post by Sergius14 on 2010-10-05
Check at the ESXi what Network Driver is being used for that machine.

Maybe it is missing or being used the wrong one.

Also you can try to remove the virtual network card, reboot the linux and adding a new one (and rebooting again).

The Flexible adapter shoud be ok with Ubuntu. I use them.

---

### Post by jonc101 on 2010-10-05
I resolved it by removing eth0 from /etc/network/interfaces and then adding eth1 to it.

eth1 had been picked up by the system but it wasn't showing when running ifconfig because I wasn't using the -a switch.

everything is good now.

---

