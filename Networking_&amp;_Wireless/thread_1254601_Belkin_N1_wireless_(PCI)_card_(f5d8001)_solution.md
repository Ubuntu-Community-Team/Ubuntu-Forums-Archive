---
title: "Belkin N1 wireless (PCI) card (f5d8001) solution"
date: 2009-08-31
forum: Networking &amp; Wireless
---

### Post by gnudoc on 2009-08-31
I've seen several threads here and elsewhere with people trying but failing to get this wireless card working. To be fair I've not seen any very recent threads, so perhaps everyone has it working now. In any case, here's how I got it running.

If anyone would like step by step instructions, let me know.

update your repos then sudo aptitude install ndisgtk unshield (ndisgtk didnt work for me but it may for you). You may also need cabextract - i think it comes as default but i cant remember.

lspci -nn gave me the right pciid to be 11ab:2a02

find the card at the ndiswrapper wiki ([http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page)) - the page I found useful was [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Belkin_F5D8001v2](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Belkin_F5D8001v2). use the instructions there to download the windows driver package and extract the inf file. You will need unzip, cabextract and unshield in that order. The inf file lives in Disk1/Win2KXP_Target. Copy the inf file and netmw145.sys into any folder then run sudo ndiswrapper -i NetMW14x.inf in that folder.

Then sudo depmod -a followed by sudo modprobe ndiswrapper

Hey presto.

My only problem, however, was that for some reason this driver won't let me use WPA. Bah! Anyone got any ideas.

---

### Post by gnudoc on 2009-08-31
Just a thought - I've not had to use ndiswrapper for a long long time. Is there a generic issue with ndiswrapper and wpa?

---

### Post by bkratz on 2009-08-31
> **gnudoc said:**
> Just a thought - I've not had to use ndiswrapper for a long long time. Is there a generic issue with ndiswrapper and wpa?

I have used Ndiswrapper with my Dlink card through several iterations of Ubuntu.  I use WPA2 and have no problems. Although I admit I never did get it to work with WEP!

---

