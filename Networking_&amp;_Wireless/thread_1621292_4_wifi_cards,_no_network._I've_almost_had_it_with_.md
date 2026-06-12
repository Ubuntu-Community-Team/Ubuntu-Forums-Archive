---
title: "4 wifi cards, no network. I've almost had it with Ubuntu"
date: 2010-11-14
forum: Networking &amp; Wireless
---

### Post by mr_si on 2010-11-14
:(

Last week my PCI card, which had always been a bit odd about connecting, (didn't like a \ in the password), stopped connecting at all. It sits there handshaking for 30 seconds and throws up the password requester again. If I turn off encryption it doesn't connect either. This lists as Atheros AR2413 802.11bg NIC. 

Yesterday's effort. Bought a new wifi dongle with known Linux support. [http://www.ebuyer.com/product/161823](http://www.ebuyer.com/product/161823)

My UB box just never lists it, let alone connect with it. I tried it on my laptop which does list it but doesn't ever give me the option of connecting with it. (It says 'disconnected' and doesn't list any networks). It lists Ralink 802.11 WLAN. lsusb says nothing.

Today I did a clean install of 10.04 on the desktop box with both the Atheros and the ralink dongle. The Atheros fails to handshake, the ralink shows in the network list but doesn't offer any networks to connect to. 

If I take out the atheros pci card then ralink doesn't get listed even. 


Various googling has lead to me downloading various tar packages which need MAKEing; without fail they wont build (can't find this or that header, struct undefined blah de blah) (I'm a C++ dev so quite capable of building packages, albeit under windows).

What next? The amount of time I've wasted on this problem could've paid for an XP license by now. 

I've got two other network cards (1 pci 1 usb I don't think they offer out of the box linux support so lets just leave them be).

---

### Post by bkratz on 2010-11-14
Perhaps the last post in this thread will help with your "building"

[http://ubuntuforums.org/showthread.php?t=1551567](http://ubuntuforums.org/showthread.php?t=1551567)

---

### Post by kumoshk on 2012-01-24
I need a USB wireless network card that works out of the box with Ubuntu 11.10. Any ideas?

Right now I'm still using Ubuntu 9.10 (Karmic). I have a Ralink 802.11 b/g/n one that worked in Karmic after installing backported modules. I'm still trying to figure out a way to get that to work on 11.10, but it would be nice to know if there are any that work out of the box.

---

