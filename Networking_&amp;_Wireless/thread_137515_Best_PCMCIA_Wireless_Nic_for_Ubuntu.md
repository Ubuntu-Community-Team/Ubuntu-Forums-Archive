---
title: "Best PCMCIA Wireless Nic for Ubuntu?"
date: 2006-02-28
forum: Networking &amp; Wireless
---

### Post by Jakanden on 2006-02-28
Hey all,

I have been having nothing but problems with my Netgear MA521 PCMCIA (RealTek Chipset) card and have yet to get it working. 

I am looking into getting a new one (I want to go 802.11g anyway) and was curious for suggestion of good cards that do not seem to have difficulties in setup. Any suggestions are appreciated =)

---

### Post by bikeboy on 2006-02-28
These might help. I came across them in my research for the same thing recently. I use ndiwrapper for my card but am going to get a ralink based one soon and give mine to another computer in the house that uses windows.

[http://www.fsf.org/resources/hw/net/wireless/cards.html](http://www.fsf.org/resources/hw/net/wireless/cards.html)
[http://ralink.rapla.net/](http://ralink.rapla.net/)
[http://rt2x00.serialmonkey.com/wiki/index.php/Hardware](http://rt2x00.serialmonkey.com/wiki/index.php/Hardware)

---

### Post by jannol on 2006-02-28
I recommended netgear wg511 to my brother and it works great.

Install is easy, install ndisgtk, install driver, go to network settings and set up wep.

---

### Post by Jakanden on 2006-02-28
Yeah I have read multiple threads here on the card and had nothing but problems with Ndiswrapper and I give up. Thanks for the info about the alternate cards though as that is what I am looking for =)

---

### Post by Zodiac on 2006-02-28
Whoa.... sorry bout that.

---

### Post by Jakanden on 2006-03-04
[QUOTE=jannol]I recommended netgear wg511 to my brother and it works great.

Install is easy, install ndisgtk, install driver, go to network settings and set up wep.[/QUOTE]

Thanks for the info. Unfortunately according to [this](http://www.tigerdirect.com/applications/searchtools/item-details.asp?EdpNo=516353&Tab=2&NoMapp=0) it does not support WPA which is what I use =(

Any other suggestions?

---

### Post by jannol on 2006-03-05
[QUOTE=Jakanden]Thanks for the info. Unfortunately according to [this](http://www.tigerdirect.com/applications/searchtools/item-details.asp?EdpNo=516353&Tab=2&NoMapp=0) it does not support WPA which is what I use =(

Any other suggestions?[/QUOTE]

WG511 V1 needs a firmware upgrade and possibly newer driver but the WG511 V2 does support wpa right out of the box. The WG511IS is V2 but I do not know of the others. But I haven't tried wpa on it myself so I don't know if it is hard work.

However after I looked it up a bit it might not be the best card, many people seem to have issues. Maybe I was lucky or rather my brother since it works great.

good luck anyways, let us know what you buy and how it works.

---

### Post by hajk on 2006-03-06
Get the NetGear WG511T PC-Card (PCMCIA) -- the "T" is important -- it has the Atheros chipset. Works out-of-the-box with the madwifi driver in the linux-restricted-modules package for your kernel version. Bought it after trolling these forums some time ago, never regretted it.

---

### Post by Skye on 2006-03-06
I'm not quite so sure about the WG511T.  I have one, and I got it working once, but after upgrading to Dapper, it doesn't work with WPA.  There's a thread about it [here,]("http://www.ubuntuforums.org/showthread.php?t=140222") where someone with breezy is having a similar problem.

---

### Post by ssam on 2006-03-06
make sure you have a look at [https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards)

(and for everyone else make sure the info about card you have tried is correct)

i bought a ralink 2500 card from [networkned.co.uk]("http://networkned.co.uk/hardware.php") who guarantee linux compatability.

---

### Post by Jakanden on 2006-03-19
Thanks for the information all! I will be looking into these cards and getting one soon =)

---

