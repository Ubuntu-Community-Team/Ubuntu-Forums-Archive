---
title: "Unstable Wireless on Netbook Sony VPCW12M1E"
date: 2009-11-16
forum: Networking &amp; Wireless
---

### Post by Samlowry84 on 2009-11-16
Hi all

So I just bought the Sony VAIO netbook VPC-W12M1E, everything works pretty fine, exept that i got an unstable wireless connection at home but still workable. However I tried at office and I hardly connect to the wireless network there.

here what i get from "lspci" command
> 
02:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
0a:09.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0a:09.1 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)


From the thread I read on the forums, and from my coleague (boss of software develoment...) it should be the driver of my wireless board. Any help would be greatly appreciate.
Thanks

---

### Post by Samlowry84 on 2009-11-17
Hi after few search i found the solution in french here
[http://forum.ubuntu-fr.org/viewtopic.php?pid=2792314](http://forum.ubuntu-fr.org/viewtopic.php?pid=2792314)
**[SIZE=2][08/07/2009, at 20:29]("http://forum.ubuntu-fr.org/viewtopic.php?pid=2792314#p2792314")[/SIZE]**

It says is kernel issue, Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) ath9k, which is not supported by the kernel 2.6.29. the kernel used by Ubuntu 9.04 is the 2.6.28-13.
you can install the new kernel with : [http://doc.ubuntu-fr.org/kernel_2.6.29](http://doc.ubuntu-fr.org/kernel_2.6.29).
seems to work out

or i found an other method here
[http://wireless.kernel.org/en/users/Drivers/Atheros](http://wireless.kernel.org/en/users/Drivers/Atheros)

---

