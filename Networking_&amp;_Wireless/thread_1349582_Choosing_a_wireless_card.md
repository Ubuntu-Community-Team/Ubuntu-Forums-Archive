---
title: "Choosing a wireless card"
date: 2009-12-08
forum: Networking &amp; Wireless
---

### Post by lduperval on 2009-12-08
Hi,

I had a Netgear WG511 PCMCIA card and it looks like it's sorta blown, so I am going to get another one. At the same time, I will probably get a new wireless router which supports g&n to replace my B modem.

My question: what card (or brands) should I strive for if I have Jaunty installed and am looking at eventually upgrading to Karmic?

I looked at the Wiki but based on the forums, there are so many wireless issues moving from Jaunty to Karmic that I am a bit apprehensive at the prospect. It's pretty difficult to tell from the tables, if the cards have been tested on Karmic or Jaunty.

Any recommendations?

Thanks,

L

---

### Post by teward on 2009-12-08
Hi, thanks for asking this question.  But before *I *can answer, I need a bit more information about your computer, such as make, model, specs, etc.

Because if the device is compatible with only your OS and not your hardware, you're stuck with nothing.

---

### Post by lduperval on 2009-12-08
It's a Toshiba Satellite A10. It's about 4 years old, I think. Maybe a bit more. 512MB, it has an internal TI PCI controller for the internal wireless (I think), but that one is showing issues as well.

L

---

### Post by teward on 2009-12-08
Well, for starters, you might consider buying a new PCMCIA card for this, I'd push Linksys if they were doing better, but any real D-Link or Linksys PCMCIA card will work (at least is *should* if you can get drivers).

As for drivers for the above, they usually have Windows drivers, and you can get them to work on Linux with ndiswrapper.


Beyond that, not much I can tell you.  Not many companies produce both windows and linux drivers, especially not Linksys (they pressure users to use Winblows :P)

---

### Post by peepingtom on 2009-12-08
Avoid NDISWrapper (used to make Windows drivers compatible with Linux). It's a source of headaches and won't ever support some of the advanced features that are being added to Linux WiFi drivers (like using your wifi card to connect to multiple networks simultaneously, or function as a router). It definitely isn't "plug and play".

Get a card with an Atheros chipset, they have great Linux support through MadWiFi and are extremely popular. Atheros even contributed a significant amount of code toward MadWifi. Avoid Marvell and Broadcom chipsets like the plague, they have terrible support for Linux. Realtek is not very good, either.

if you want to be very careful, buy online from a store that tells you the chipset. Then check [http://madwifi-project.org/](http://madwifi-project.org/) to see how the support is for that chipset.


Ralink also has good linux driver support, not as good as Atheros but pretty much all their chipsets function well under Linux.
Some of their inexpensive miniPciE cards can be purchased at monoprice, which also sells very inexpensive cables.
[http://www.monoprice.com/products/subdepartment.asp?c_id=105&cp_id=10501](http://www.monoprice.com/products/subdepartment.asp?c_id=105&cp_id=10501)

---

### Post by diablo75 on 2009-12-09
If you can accept a PCMCIA card, I would HIGHLY recommend a D-Link WNA-2330.  You can find it on ebay for about 30 bucks.  This card has worked out of the box with no drivers needed for installation since Ubuntu 7.10 or so.  Just plug it in, and you're online.  It's worked GREAT for me.  It has an atheros chipset too, if you're interested in knowing that.

---

