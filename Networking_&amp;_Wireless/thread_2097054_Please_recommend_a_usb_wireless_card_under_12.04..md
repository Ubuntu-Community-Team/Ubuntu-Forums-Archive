---
title: "Please recommend a usb wireless card under 12.04."
date: 2012-12-21
forum: Networking &amp; Wireless
---

### Post by waterloo2005 on 2012-12-21
Please recommend a usb wireless card under 12.04.
Thanks

---

### Post by 2F4U on 2012-12-21
Did you already look at the Ubuntu certified components list?

[http://www.ubuntu.com/certification/catalog/category/WIRELESS/](http://www.ubuntu.com/certification/catalog/category/WIRELESS/)

---

### Post by waterloo2005 on 2012-12-22
> **2F4U said:**
> Did you already look at the Ubuntu certified components list?

[http://www.ubuntu.com/certification/catalog/category/WIRELESS/](http://www.ubuntu.com/certification/catalog/category/WIRELESS/)

I see it. But they are almost for pci, not usb.

---

### Post by ahallubuntu on 2012-12-22
> **waterloo2005 said:**
> Please recommend a usb wireless card under 12.04.
Thanks

What are your criteria?

You can get very cheap tiny USB wireless cards based on the Realtek 8188/8192CU chipset - but these cards are only 150Mbps (and only 2.4GHZ).  And the kernel driver in both 12.04 and 12.10 doesn't work right, so you have to build your own driver from Realtek's website.  But it's fairly easy  to build if you don't mind opening a terminal.

The big upside is probably the price (under $10 USD on eBay or Amazon).  I've bought a handful of these little cards to use for projects.  They are handy to have around, plenty fast enough for basic web stuff.  Wireless range is better than you would think without much of antenna.  I have one in a media center box downstairs and the router is upstairs, and I stream web media with it all the time.

I have another 150Mbps/2.4GHZ USB card (not a "small" USB, about the size of a regular USB thumb drive) based on the Ralink RT2870/RT3070, and that one seemed to work automatically in the recent versions of Ubuntu.  Mine is a Tenda W311U.

I don't have any 300Mbps USB cards at the moment, so I can't recommend one.

---

### Post by waterloo2005 on 2012-12-24
Thanks first.
I already have a rtl8192cu card. But it makes me sad.
I try to install driver from realtek site, and I do like such instructions. But everytime I plug the card, my system dies.
Now I have got tp-link tl-wn822n, which is 300M and can work automatically in 12.04.

---

### Post by haqking on 2012-12-24
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

[http://linuxplained.com/linux-compatible-usb-wireless-adapters-2012/](http://linuxplained.com/linux-compatible-usb-wireless-adapters-2012/)

---

### Post by agillator on 2012-12-24
Do you mean a usb CARD or usb ADAPTER? If you are actually looking for an adapter, i.e. something to plug into a usb port on the machine rather than a card to install in the computer, there are a number available. I am currently using the Belkin N300 and it seems to work without a problem. I would stay away from the Belkin N600, though, unless someone who is using one pitches in and says it is ok. Comments I have read seem to indicate it doesn't play well with Linux (yet). Also stay away from the LinkSys AE2500 for the same reasons. Using NDISWRAPPER can be an option to get something to work (the AE2500 can work this way) but personally I find that to be more trouble than it is worth when there are others available that do work. As a last resort, though, . . . .

---

