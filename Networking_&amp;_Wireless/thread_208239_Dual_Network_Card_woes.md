---
title: "Dual Network Card woes"
date: 2006-07-03
forum: Networking &amp; Wireless
---

### Post by Errol Errolson on 2006-07-03
Hello all, I'm running a dual network card setup, one for LAN and one for WAN, the problem is that WAN connectivity is sporadic at best while LAN remains consistently accessible.

One network card is onboard, a VIA Rhine II (eth1), the other is a pci based card, I think a SIS of some description (eth0).  The onboard is set up for WAN, the pci for LAN.

We've ruled out internet problems (the same line is used for another linux box running a similar setup but using FC2, which is still accessible while the Ubuntu box isn't), various network hardware (replaced all the routers and firewalls) and pretty much everything else.

Any ideas what would cause the intermittent connectivity problems on just one card?

Cheers,
Errol

---

### Post by jml on 2006-07-03
Its possible that you have a defective card.  Can you swap the card out for another one and see if the problem persists?

---

### Post by Errol Errolson on 2006-07-03
Hello, yes, we did swap the PCI card with another that was an identical make and model and still the problem remains.

So, either there's a problem with that make of card (if someone could tell me a way of finding out hardware from a bash prompt I'd be able to tell you more than "it's a SIS") or there's some issue with the whole hardware configuration (we actually have this problem on two identical machines).

-Errol

---

