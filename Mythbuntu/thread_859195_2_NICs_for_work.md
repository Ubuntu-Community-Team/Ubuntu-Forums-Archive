---
title: "2 NICs for work"
date: 2008-07-14
forum: Mythbuntu
---

### Post by enrique.lopez on 2008-07-14
I've 2 NICs 1 for external (internet-eth0 192.168.1.2 gateway 192.168.1.1) and 2 (internal LAN eth1 192.168.80.1) i want run DHCP in eth1 but no possible y choose DHCP server in MCC mythbuntu but the client no boot in PXE mode. Any solutions?
Thanks

---

### Post by foxbuntu on 2008-07-14
> **enrique.lopez said:**
> I've 2 NICs 1 for external (internet-eth0 192.168.1.2 gateway 192.168.1.1) and 2 (internal LAN eth1 192.168.80.1) i want run DHCP in eth1 but no possible y choose DHCP server in MCC mythbuntu but the client no boot in PXE mode. Any solutions?
Thanks

You can exit the frontend and you will find Network Manager is in the corner as always in a Ubuntu install. You can also Select Settings Manager from the menu on the desktop to setup your NIC any way you wish.

---

### Post by enrique.lopez on 2008-07-14
> **foxbuntu said:**
> You can exit the frontend and you will find Network Manager is in the corner as always in a Ubuntu install. You can also Select Settings Manager from the menu on the desktop to setup your NIC any way you wish.

The solution edit dhcp.conf in /etc/ltsp and cha nge the setting manually.
Thanks

---

