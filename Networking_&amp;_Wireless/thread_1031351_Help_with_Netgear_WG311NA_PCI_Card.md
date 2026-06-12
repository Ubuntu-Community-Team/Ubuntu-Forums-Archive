---
title: "Help with Netgear WG311NA PCI Card"
date: 2009-01-05
forum: Networking &amp; Wireless
---

### Post by AJESQ on 2009-01-05
Just added a wireless pci card to my ubuntu system and I can not get it to work. I have gone through several forums and still can not have it working. I downloaded the drivers for the x64 and did the  WG311v3.sys swap out from a forum I had read... still nothing

Here is what I have:
alex@AJS-Ubuntu:~$ ndiswrapper -l
wg311v3 : driver installed
	device (11AB:1FAA) present

alex@AJS-Ubuntu:~$ lspci | grep Marvell
01:09.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

alex@AJS-Ubuntu:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.


There was something in the dmesg about a failure and something about unmounting the network card but for some reason I can not initiate that error again.

Help!

---

