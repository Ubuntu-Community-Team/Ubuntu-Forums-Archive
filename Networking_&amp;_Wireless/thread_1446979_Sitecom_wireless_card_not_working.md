---
title: "Sitecom wireless card not working"
date: 2010-04-04
forum: Networking &amp; Wireless
---

### Post by Hythebob on 2010-04-04
I've just installed Ubuntu (Koala) on an old (but worthy) Toshiba laptop. It's got a Sitecom WL-140 wireless card.
(BTW I'm new to Ubuntu, but an old hand at Solaris)
Can't get the card to work, although I think It's nearly there. 
nm-tool shows driver is p54pci. The activity light shows an orange light occasionally. State is disconnected.
I'm not really sure whether I should be using the supplied driver (p54pci) or the Windows driver for this card and ndiswrapper. I've installed the Windows driver with ndiswrapper thinking this may fix it but no.
ndiswrapper -l     says wlancig: driver installed and device (1260:3886) present.
Perhaps I've confused it.
I've googled loads but struggling now.
Can anyone help?

---

### Post by chili555 on 2010-04-05
> Perhaps I've confused it.Let's look around a bit and see. Please post:```
lsmod | grep -e p54 -e ndis
iwconfig
dmesg | grep -e p54 -e wlan
```Thanks.

---

