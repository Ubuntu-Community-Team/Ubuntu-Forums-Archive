---
title: "How do I make Ubuntu forget old network cards?"
date: 2010-06-03
forum: Networking &amp; Wireless
---

### Post by whein on 2010-06-03
Mostly a cosmetic question since I have a workaround, but is there a way to make an install "forget" network cards that used to exist in the system but have since been removed?  In this case I have a computer that had a motherboard ethernet adapter and a second PCI networking card, as eth0 and eth1.  Then the motherboard went south and I took the same hard drive and plugged it into a new motherboard which had a built in ethernet adapter.  This became eth2.  Now I finally received my replacement motherboard (from NewEgg, naturally) and everything is working fine but this on board adapter insists on being called eth3.  Is there a way to force it to be eth0, presumably by removing any record of the previous adapters?  Yes, I could just leave it as eth3 and everything works fine but I don't like it.

-Will

---

### Post by Zakhafr on 2010-06-03
Look at :

/etc/udev/rules.d/70-persistent-net.rules

It is where the associations are kept
*(... or so do I think !)*

Remove the one that are useless for you (or remove all, they will be recreated in order)

As a precaution first save the file elsewhere in case you do it wrong!

---

