---
title: "What Printer/AiO To Buy For Networking?"
date: 2013-03-16
forum: Networking &amp; Wireless
---

### Post by sajanNOPPIX on 2013-03-16
Having gone Ubuntu everywhere on all computers/laptops, I'm still missing a printer/scanner at my place.  I usually just email the local print store or stop by to scan things and get things done.  It's on the way for me to everything, so that's been fine.  However, I now want to buy a decent printer, scanner w/ document feed for myself.  I want it to either be connected via ethernet or wifi to my router, and most importantly I want it to play nice with Ubuntu over the network.

Anyone have any suggestions as far as manufacturers or particular protocols features I should look for?  Or will most all network printers on the market work reasonably well with Ubuntu without too much fuss?

Thanks.

---

### Post by Sef on 2013-03-16
Check here for supported [HP models]("http://hplipopensource.com/hplip-web/supported_devices/index.html").

---

### Post by sudodus on 2013-03-16
I'm happy with a Brother black and white network laser printer, HL-2250DN. You can download linux drivers at Brother's web site.

*Edit*: and I have an old Epson perfection 3200 photo scanner, that works out-of-the-box with the built-in linux drivers.

---

### Post by pdc on 2013-03-17
[http://www.google.co.nz/cloudprint/learn/](http://www.google.co.nz/cloudprint/learn/)

things such as this as coming too;

eg Canon are now releasing printers that are google cloud ready

[http://www.usa.canon.com/cusa/consumer/standard_display/cloudprint](http://www.usa.canon.com/cusa/consumer/standard_display/cloudprint)

......if you were to choose Canon, it is worth checking drivers are available

[http://support-asia.canon-asia.com/?personal](http://support-asia.canon-asia.com/?personal)

the MG4200 series have excellent driver support: 32bit and 64bit packages; in .deb and .rpm format

we recently installed an MG2100 series Canon printer: it cost about $US40 equivalent: increasingly, the hardware cost will be a small factor: repeated ink costs if used a lot will be the bigger part of the whole package;

---

### Post by kurt18947 on 2013-03-17
The newer Brothers work quite well with Ubuntu.  The thing that might be a little offputting is that installation is done via the command line.  There's an installer script which works quite well for installing the printer portion of AIOs but the scanner portion may (will) require some command line input.  It was interesting when installing 13.04 that a wirelessly  networked MFC-J430W 'just appeared' as an installed printer with no intervention on my part.  And it printed without configuration.  Here's the printer installer script:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104)

---

