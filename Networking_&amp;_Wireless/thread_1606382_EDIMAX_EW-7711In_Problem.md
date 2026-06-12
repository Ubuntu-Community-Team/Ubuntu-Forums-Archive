---
title: "EDIMAX EW-7711In Problem"
date: 2010-10-26
forum: Networking &amp; Wireless
---

### Post by nickbabenko on 2010-10-26
Yesterday I got the EDIMAX EW-7711In PCI wireless network card and I've had so many problems installing it, it even says it has Linux support on the box but I've had no such luck.

I started on the edimax website, [www.edimax.co.uk](www.edimax.co.uk), there is edimax.com but it doesn't have the links for an ubuntu driver. Followed their instructions, also from their website and the network card showed no life.

After a lot of google searching and and installing a few different drivers, I managed to get the device to display in network tools "Unknown Interface (ra0)" I also installed Wicd, which seems to use the wireless card fine but the networks it finds don't show very well, my network is only sometimes their at 100%, some times it drops the signal strength or isn't their at all. If I try to connect I get a bad password response, so it must be talking with my router. The network card still doesn't show in the Ubuntu network menu either.

I managed to installed the Ralink RT3062 driver, which is what made Ubuntu finally recognise the wireless card, although on the edimax website it gives a link to RT3070.

Any help, links, anything would be amazing.

---

### Post by benjmullen on 2011-09-25
i know this is a late reply but i have tryed everything to install this wireless card but nothing seems to work, i did install 10.04 LTS because edimax said that their driver supports that but it still doesnt work.
i extracted the driver tar.gz
 tar xvjf file.tar.gz
 cd file
 ./configure
 make
 su
 make install

but when i got to the point of ./configure it says there is no such directory...

---

