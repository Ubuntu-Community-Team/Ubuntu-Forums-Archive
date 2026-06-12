---
title: "pci dvb card for viewing free sat  or sky tv"
date: 2010-01-18
forum: Multimedia Software
---

### Post by markp1989 on 2010-01-18
im looking for a pci card to view sky through that will work with ubuntu.

a guy here got it working , but i dont know if it is possible with ubuntu 

[http://www.satellites.co.uk/forums/satellite-pc-card-receivers-internet-satellite/95167-htpc-sky-hd-uk-working-also-viewing-card-has-been-out-my-sky-box-months.html](http://www.satellites.co.uk/forums/satellite-pc-card-receivers-internet-satellite/95167-htpc-sky-hd-uk-working-also-viewing-card-has-been-out-my-sky-box-months.html)

if sky tv is a issue on a pc, then i will happily give free sat ago, i just want a card that will work well with ubuntu 

thanks markp1989

---

### Post by jimmers on 2010-01-19
This may or may not be of any use to you, but worth a try.
Open up the web page below,, and search for TV Tuner Cards.
  	 	 	 	 	 	  [www.maplin.co.uk/Stores](www.maplin.co.uk/Stores).

---

### Post by steefjeqv on 2010-01-19
Hi,

Freesat is possible. I've been watching Freesat for about 3 years now on my Ubuntu based settop computer.
Do you need a smart card to watch Sky ? If that's all you need I can advise a KNC1 DVB-S card + cam module (they're also sold under the Mystique brand). Expect some configuring and trouble shooting though and no garantuee it'll work.

All of these cards will work :

[http://www.linuxtv.org/wiki/index.php/DVB-S_PCI_Cards]("http://www.linuxtv.org/wiki/index.php/DVB-S_PCI_Cards")
[http://www.linuxtv.org/wiki/index.php/DVB-S_PCIe_Cards]("http://www.linuxtv.org/wiki/index.php/DVB-S_PCIe_Cards")
[http://www.linuxtv.org/wiki/index.php/DVB-S2_PCI_Cards]("http://www.linuxtv.org/wiki/index.php/DVB-S2_PCI_Cards")
[http://www.linuxtv.org/wiki/index.php/DVB-S2_PCIe_Cards]("http://www.linuxtv.org/wiki/index.php/DVB-S2_PCIe_Cards")

Easiest application to use is Kaffeine.

If you're looking for a true settopbox feel there's only one app that does the trick for me : VDR (the Linux Video Disk Recorder). It can be enriched with more than a hundred plugins (including full freesat epg).
It's available in the Ubuntu repo's.
There's a better, recent version (HDTV,XBMC, VDPAU + more plugins ....) put together by the guys from the VDR-Team (thanks again to all of you if you're reading this).

[http://www.linuxtv.org/vdrwiki/index.php/Main_Page]("http://www.linuxtv.org/vdrwiki/index.php/Main_Page")
[https://launchpad.net/~the-vdr-team/+archive/vdr-ubuntu-karmic]("https://launchpad.net/~the-vdr-team/+archive/vdr-ubuntu-karmic")

Latest feature by the VDR-team : an Ubuntu based VDR (+XBMC) distribution, called yaVDR.

[http://www.yavdr.de/]("http://www.yavdr.de/")

By the way, if you want HDTV the best results you can have are by using Nvidia graphics (VDPAU acceleration). Supported as of the 8xxx series (you'll need 512 mb graphics memory).

Hope this helps a bit.

Greetings,
Steven


Greetings,
Steven

---

