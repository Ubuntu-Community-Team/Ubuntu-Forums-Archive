---
title: "DHCP server stops working"
date: 2009-05-27
forum: Networking &amp; Wireless
---

### Post by map7 on 2009-05-27
About once a week my DHCP server goes down and I cannot see what the problem is.

I'm running Mythbuntu 8.10 with PXE diskless clients which when booted first look for a DHCP server on the network.  I have multiple PXE diskless clients which all freeze in the middle of what ever they were doing when the this problem occurs.

The dhcp server still says it's running.  If I restart the dhcp server my diskless clients still cannot boot.  If I restart the computer as I did the first time it starts working again.  This time I've left it in the problem state so I can pin point the problem.

I'm running an ASUS A8V Deluxe motherboard with a brand new ASUS NX1101 PCI Gbit Network Card.  I've tried changing cables, a different PXE client (which I know works usually), restarting the switch I'm using.  

I'm starting to point my finger at the ASUS NX1101 card, my next step is to go a purchase another network card and test with that.  

Am I on the right path?  
Should I be checking anything else before hand?

---

### Post by Iowan on 2009-05-27
Since it only happens once/week, I presume it's not a power management option in the BIOS that's shutting down the interface...

---

