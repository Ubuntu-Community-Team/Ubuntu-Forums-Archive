---
title: "Can't use ppp0 and eth0"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by emarvets on 2008-12-08
<Running Ubuntu 8.10 x64 on a T61 laptop>

I've been trying to setup my Verizon USB card.  I finally was able to get online with ppp0 by deleting eth0 in the Network Connections.

What I've tried so far:

I began by using wvdial, which reported that it worked (connected, returned IP address, DNS servers, etc.), but when I tried to browse a website, nothing would happen.  Same thing when I tried to ping anything.

Then I went with gnome-ppp.  Again, was able to successfully connect to the network, but could not browse internet or even ping an address.

I finally figured out that I could setup the mobile connection by right clicking on the networking icon in the upper right hand corner.  Same result.

I was reading someone's post of having issues with eth0 and ppp0 and decided to remove eth0 and see what would happen.  I was immediately on the internet.

I need eth0 (home network) and ppp0 (only connection to the internet) at the same time.  Any ideas?

---

### Post by Iowan on 2008-12-08
You may need to manually configure /etc/network/interfaces.  At least a couple of versions ago, Network Manager would only enable one interface at a time.

---

