---
title: "Server 12.04 fails to respond to client ARP requests during PXE boot"
date: 2013-05-31
forum: Networking &amp; Wireless
---

### Post by kavernon on 2013-05-31
I've recently installed and configured ubuntu server 12.04 as my DRBL/Clonezilla server and am having some issues with getting clients to PXE boot.  The client is cabled directly to the secondary network card, so no router/switch issues.  It appears that server simply ignores ARP requests.  The client will get an IP successfully from DHCP, but complains of 'no response to arp requests' and thus tftp fails and client abandons network boot in favor of local hdd.  Any tips/hints/suggestions greatly appreciated.

---

### Post by bab1 on 2013-05-31
> **kavernon said:**
> I've recently installed and configured ubuntu server 12.04 as my DRBL/Clonezilla server and am having some issues with getting clients to PXE boot.  The client is cabled directly to the secondary network card, so no router/switch issues.  It appears that server simply ignores ARP requests.  The client will get an IP successfully from DHCP, but complains of 'no response to arp requests' and thus tftp fails and client abandons network boot in favor of local hdd.  Any tips/hints/suggestions greatly appreciated.

Where is the DHCP server located (router or DRBL/Clonezilla server or...) ?  What is the IP address of the server you mentioned?  What is the IP address of the *" client is cabled directly to the secondary network card"*?  Usually ARP problems mean the 2 hosts are not on the same network.

---

