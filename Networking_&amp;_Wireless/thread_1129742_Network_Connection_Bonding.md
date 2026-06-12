---
title: "Network Connection Bonding"
date: 2009-04-19
forum: Networking &amp; Wireless
---

### Post by collinpetty on 2009-04-19
Hello, I am currently a college student, our internet is capped by mac address. Each mac gets 3 mb/s of bandwidth up and down.  What I am trying to do (mostly for learning purposes) is bond a number of virtual network connections together from a virtualbox Ubuntu 8.10 install.  I have the virtual computer set up to have 4 Ethernet adapters each using the host adapter.  Virtualbox is acting as a networking switch so the virtual install of Ubuntu actually has 4 separate mac address, each of which can be used to download files at a full 3 mb/s at the same time.  I am trying to bond these connections together to form one virtual connection with an increase throughput, I understand that this would not benefit on downloads that require a single connection but for downloading something such as a torrent I would imagine that it would be almost perfectly efficient.  The problem is that using other bonding methods, the bond module changes the mac address of all the network interfaces to the same mac.  I need to set up a sort of round robin system whereby connections can be made through each network adapter while each one maintains a seperate IP/macaddr.  Thank you very much for any help in advance.

---

### Post by mushroom_mover on 2009-05-01
Hi there - may I suggest you search on the keywords "broadband bonding" to see the various solutions that are commercially available. Good luck, and may there be mushrooms in your future network... :-)

---

