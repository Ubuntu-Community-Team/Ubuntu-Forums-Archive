---
title: "wireless access point"
date: 2007-12-27
forum: Mythbuntu
---

### Post by voctikal on 2007-12-27
Am wanting a wireless solution for my htpc.  Could I just get a wireless AP and use that. If so, would there be a lot of config involved?

Or should I just get a wireless card, and if so which one do you all recommend.

---

### Post by PilotJLR on 2007-12-27
Some AP's would work... some don't... depends on if they can be configured as bridges.

Better be safe and get a real wireless NIC. If you have a free PCI slot, then I would say to get anything supported by madwifi.
[http://madwifi.org/wiki/Compatibility](http://madwifi.org/wiki/Compatibility)
I've had really good results with D-Link cards with Atheros chipsets (therefore madwifi driver).

---

### Post by voctikal on 2007-12-29
Would any of these be plug n play or would I need to find a certain driver?

---

### Post by PilotJLR on 2007-12-29
Many are... with Atheros chips and madwifi for a driver, it should work out of the box with Ubuntu, since Ubuntu includes the madwifi package.

I've had several Dlink cards with atheros chipsets, and so far all have been plug and play with Ubuntu

---

### Post by voctikal on 2007-12-30
Anyone recommend a particular card?

---

### Post by ozybushwalker on 2007-12-31
I used a Gigabyte GN-WB01GS USB wireless card (uses a Ralink chipset) which worked "out of the box" with Kubuntu 7.10.

For another application I was looking for a wireless card that could operate as an Access Point (the Ralink driver doesn't currently support operating as an Access Point) and an Atheros card seemed the most effective way to go. I looked up the list referred to earlier [http://madwifi.org/wiki/Compatibility]("http://madwifi.org/wiki/Compatibility") and went looking for sources of a number of cards without success other than the TP-Link. A few days ago I ordered a couple of WN651G cards but they haven't arrived yet so can't comment on them.

A problem with DLink (and Linksys and Netgear) cards is that the same model name gets reused for cards with a different chipset so if you buy a card with one of those brands you can't really be sure what chipset is used until you actually have the card and can probe it.

I found a couple of ebay sellers of the TP-Link cards and a few online shops. A search with one of the "shopbot"services would probably help you track down a supplier.

---

### Post by voctikal on 2007-12-31
Thanks for the reply.

Ill see what I can find

---

