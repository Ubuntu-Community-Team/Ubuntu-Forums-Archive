---
title: "Linksys Wireless card  DISABLED in Ubuntu 8.1"
date: 2009-03-12
forum: Networking &amp; Wireless
---

### Post by ubungler on 2009-03-12
Hi I'm hoping someone can give me a push in the right direction here.
I've just installed ubuntu 8 and it seems like the network card is by default disabled.
I've got a Linksys PCI card
product: BCM4306 802.11b/g Wireless LAN Controller
version: 03

I've set up my wireless network details using the gui network tool, but there's no connection being established.

I did the command lshw which told me
*-network:0 DISABLED
     description: Wireless Interface

Is there some straightforward way to enable this?

---

### Post by jdelasalas on 2009-03-12
Did you install the drivers?  I noticed that my laptop recognized my card but couldn't connect until used ndiswrapper.

---

### Post by ubungler on 2009-03-12
I haven't done anything to explicitly install drivers, but something I'd read led me to believe they might have been included into the kernel.

Is there a straightforward guide to it somewhere? I've searched but so many people have had problems with wireless it's hard to see what's relevant!

---

### Post by Ayuthia on 2009-03-12
If you have a working connection in Ubuntu, go to System->Administration->Hardware Drivers and activate the Broadcom b43 module.  That is the wireless module for your card.  The module needs to have a portion of the proprietary firmware to make it work so this is why you have to download the firmware.

If you don't have a working connection, you can try this [post]("http://ubuntuforums.org/showpost.php?p=6077792&postcount=72").

Hope that helps.

---

### Post by ubungler on 2009-03-13
Thanks!
That's exactly what I needed. I don't have a wired network connection from that PC so I followed the steps in that post and everything now works perfectly.
Fantastic :-)

---

