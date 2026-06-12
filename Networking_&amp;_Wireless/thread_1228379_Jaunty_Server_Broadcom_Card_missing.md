---
title: "Jaunty Server Broadcom Card missing"
date: 2009-07-31
forum: Networking &amp; Wireless
---

### Post by reddragonit on 2009-07-31
I had had a Dell poweredge 650 server up and running with Ubuntu prior to this post and the upgrade, using Intrepid.  The network card it uses is a PCI card, specifically a Broadcomm BCM5701 according to executing lspci.  At first I did a system upgrade to move over the Jaunty and it caused the network card to disappear.  

I found posts saying that this can sometimes happen in an upgrade but it was not common, and given that I had not started using the server yet, I felt that I should simply do a fresh install, which I tried with a freshly downloaded copy of the Ubuntu Jaunty server.  

During the installation the system informed me that it could not locate any network interfaces, though the card shows itself live, works through a Knoppix live CD.  

I have tried manually enabling the appropriate modules, forcively configuring the network card in the interfaces file and I still get unable to locate card.  Please help me with finding out why this is happening as I would prefer using Jaunty of Intrepid.

---

