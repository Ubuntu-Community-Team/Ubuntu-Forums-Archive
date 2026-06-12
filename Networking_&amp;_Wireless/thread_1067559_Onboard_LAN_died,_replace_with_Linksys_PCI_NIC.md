---
title: "Onboard LAN died, replace with Linksys PCI NIC"
date: 2009-02-12
forum: Networking &amp; Wireless
---

### Post by lightningrod66 on 2009-02-12
I have Ubuntu 8.10 server installed as LAMP server.  It was set up using the onboard LAN for networking.  That has since died and I have replaced the onboard LAN with  Linksys PCI NIC.  I disabled the onboard LAN in BIOS.  Ubuntu will not recognize this NIC.  I swapped the Ubuntu hard drive for a WinXP hard drive and it recognizes the NIC and it works great.  I have edited the /etc/network/interfaces file and changed eth0 to eth1 but that did not work.  I changed eth1 back to eth0 and still no luck.  I have restarted the network and restarted the computer - - - no luck.  What do I need to do to get this NIC recognized/configured in Ubuntu 8.10 server???

P.S.  I have also posted this problem in the "server platforms" area.  Don't know which place is actually correct.

[SOLVED] The NIC was now named eth2 (???)

---

