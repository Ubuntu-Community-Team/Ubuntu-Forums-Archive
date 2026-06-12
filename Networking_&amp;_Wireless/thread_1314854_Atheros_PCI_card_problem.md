---
title: "Atheros PCI card problem"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by cybercrypt13 on 2009-11-04
I have an Atheros AR5213A card and am trying to get madwifi to work with it to play around with Kismet.  I"m noticing a few possible problems though and wondering if anyone can help me.

FIrst if I do a lspci I'm getting a listing for Atheros AR5001X instead of my real card number.  Is this a problem and how do I fix it?

Secondly, I'm reading places talking about patching the card to get it work properly but wondering if anyone might point me somewhere to learn how to do that properly.

Thanks for any help you might provide.

glenn

---

### Post by t0mppa on 2009-11-04
> **cybercrypt13 said:**
> FIrst if I do a lspci I'm getting a listing for Atheros AR5001X instead of my real card number.  Is this a problem and how do I fix it?

Lspci doesn't care what kind of a card you have, it's only listing the chip type that card is using and more often than not, version credentials on those two don't match. Basically there's less chips and chip manufacturers than their card equivalents around and thus a bunch of cards use the same chips. So, bottom line is that it's not a problem.

My Atheros 5007 card used to be displayed as AR242x by lspci, but now on Karmic it's reported as AR5001. Thus as you can see, names change. The more important detail is the code that can be seen on **lspci -n** (or **lspci -vnn** to see both the code and the name), if you really want to uniquely identify your chip. For example:```
06:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [COLOR="Red"][168c:001c] (rev 01)[/COLOR]
```
The first part (168c) identifies the manufacturer, the second part (001c) identifies the device amidst the manufacturers products and then the revision separates different versions of the same product.

> **cybercrypt13 said:**
> Secondly, I'm reading places talking about patching the card to get it work properly but wondering if anyone might point me somewhere to learn how to do that properly.

Kismet documentation says that it only uses monitor mode and that ought to work on Madwifi without needing any patches, you can read more about that over [here]("http://madwifi-project.org/wiki/UserDocs/MonitorModeInterface"). If you're planning on using some other tools like Aircrack, then you might need patches, but they're usually well documented on the sites for said tools.

---

