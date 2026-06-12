---
title: "Linksys card with RaLink chipset"
date: 2009-04-18
forum: Networking &amp; Wireless
---

### Post by prn on 2009-04-18
Hi folks,

I've mostly used RedHat based Linux previously, but I've got a "new" box and I'd like to try Ubuntu. The box is a Dell Dimension 4550 and I've added RAM and HD space as well as a wireless card. I picked the Linksys WMP54G v.4.1 because I have gathered that the RaLink 25xx chipset in the recent versions of the Linksys PCI card is supposed to be well-supported in Linux.

So far, I have installed the RAM, new HD and PCI wireless card and then booted Ubuntu 8.10 (Intrepid Ibis) from the CD. I know that Jaunty Jackalope is due out in a few days, but I figured that it was still worth burning an Ibis CD to test things out. 

I ran the Hardware test application and confirmed that it does see a "RaLink RT2561/RT61 802.11g PCI" card in the network part of the test. Unfortunately, I can't seem to see how to get it to actually **use** the card and connect to my wireless router. At this point I don't want to mess with anything too fancy, so I have the router not broadcasting its SSID, but not requiring encryption (i.e., no WEP, no WPA). I know it's lousy security, but, especially when I'm trying to connect something that isn't cooperating, I want to minimize the number of steps that can go wrong.

Anyway, I tried the network connection app and tried to add a wireless connection, put in the SSID of the router/access point and nothing happens. 

Does anyone have a clue for the clueless?

Thanks,
Paul

---

### Post by UranUtan on 2009-04-18
Hi,

I cannot help you my linux expertise is rather low. I have a similar issue and here is what I have done to fix. Hope you would find similar solution.

Using Ubuntu 8.10 x64. My PCI Wireless card is a TP-LINK TL-WN851N which has the Atheros AR5008 chip. I have read somewhere that Atheros chips are well supported in Linux. The card was recognized by Ubuntu but I have never been successful to connect to anything. One day I searched around and tumbled on a post, I fotgot the URL but I think that led me to this page: [http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)

I followed the instructions, and by miracle, my wireless card now works OK.

---

### Post by prn on 2009-04-18
Hi UranUtan,

Thanks for the link. I looked at it and what it is is a procedure to update your Linux kernel to include otherwise unsupported wifi cards. The thing is, the drivers for the RaLink RT2x00 chipsets are supposedly already included in the current kernels. For example, the _[Main page of the RT2x00Wiki]("http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page")_ says:
> The rt2x00 drivers have been long enough in the kernel, and all major distributions have switched over to those drivers.
So I would **expect** Ubuntu to have the support for my chipset already. It may be that I am naive, but it may also be that I am supposed to do something else that I have not done yet. So I want to give the system a fair shot before I go messing around with actually replacing the kernel myself.

Thanks,
Paul

---

### Post by UranUtan on 2009-04-18
Hi Paul,

Me too I expected that the Atheros chip would be recognized and worked right away. I bough actually two cards from TP-Link. The first one TL-WN651G (Atheros AR2414) works immediately out of the box. The 2nd TL-WN851N ( Atheros AR5416, and I don't know why the chip is named with another number AR5008 ) was also recognized but cannot connect.

To tell you the truth, I don't remember exactly what I had updated. But I believe I used the page I gave the link as it looks familiar.

If you have a machine with Windows laying around, may be you can try this card just to ascertain that the card functions properly from the hardware point of view?

---

