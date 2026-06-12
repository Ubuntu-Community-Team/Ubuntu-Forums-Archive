---
title: "Wired networking stops working on Maverick or Natty"
date: 2011-05-23
forum: Networking &amp; Wireless
---

### Post by olaf_nz on 2011-05-23
Hi

I had a bizarre one on the desktop this morning - after a suspend/resume, my network adapter was disconnected with no option to reconnect.

"ifconfig eth0" showed the adapter and MAC address, but no IP. I am running Ethernet to a DSL router, so I checked cables, router, etc, but the laptop worked fine plugged in to the same cable.

I then booted into an old Live CD of 9.10 that I have, and the network (and Internet) work fine. Booted back to my Maverick install (2.6.35-28-generic) and it doesn't work. Tried all kinds of forum posts to reconfigure the network and restart the adapter, but no luck, so I downloaded Natty and tried the Live CD of that - same Ethernet symptoms - "Disconnected"!

In summary, I can boot the Live CD of 9.10 (i386 32-bit) and Ethernet will work, but the Live CD of 11.04 (i386 32-bit) will not.

Final weirdness - I finally found a forum post that said that they had had joy with turning the computer off at the wall, rather than simply turning it off - I tried that and my install again works perfectly! (I haven't tried the Natty CD, but I'm sure it will work too...)

But that's not really a solution - the old CD worked throughout, so even if there's something odd going on in the hardware of the network card, I think there's been a regression in how it is handled.

Motherboard - Gigabyte GS-MA74GMT-S2
CPU - AMD Phenom II X4 955
RAM - 4 GiB DIMM 1333MHz
Ethernet - Realtek RTL8111/8168B PCI Express Ethernet controller (onboard)
Disk - ATA Seagate ST31000528AS 1TB.

More hardware and configuration files available - I don't know what is likely to be useful, but given that it was reproducible on the Live CD's, it can't really be my configuration.

---

