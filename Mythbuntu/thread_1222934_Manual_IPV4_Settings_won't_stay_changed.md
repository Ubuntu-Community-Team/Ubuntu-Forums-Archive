---
title: "Manual IPV4 Settings won't stay changed"
date: 2009-07-25
forum: Mythbuntu
---

### Post by brian_hayward on 2009-07-25
I am running Mythbuntu 8.10 and i want to configure the machines IP address myself rather than run it in DHCP mode.  I can change the settings, and it all works, but when i re-start the machine i lose all my settings and it goes back to DHCP mode.  How can i make my changes stick?  Any help or suggestions are greatly appreciated.  Thanks.

---

### Post by ianhaycox on 2009-07-26
I found I had to remove the network-manager and network-manager-gnome apps to get my changes in /etc/network/interfaces and /etc/resolv.conf to stick

---

