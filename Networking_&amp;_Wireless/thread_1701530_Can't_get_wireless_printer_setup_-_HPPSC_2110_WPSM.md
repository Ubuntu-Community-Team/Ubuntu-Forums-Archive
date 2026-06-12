---
title: "Can't get wireless printer setup - HPPSC 2110 WPSM54G"
date: 2011-03-06
forum: Networking &amp; Wireless
---

### Post by cforput on 2011-03-06
I just installed 10.10 - the Maverick Meerkat and I'm trying to get my network printer setup.

Printer = HP PSC 2110
Wireless Print Server = Linksys WPSM54G ver 1.1

I have access to the internet so my wireless device on the laptop is working OK.

I have CUPS installed version 1.4.4.6
I do NOT have SAMBA installed

I don't know if do or do not need either of these but in reading some of the threads, both have been mentioned.

I have connected the PSC 2210 via USB to my laptop and installed it as a usb connected device. I also successfully printed a test page.

Can anyone give me guidance from here? What do I need to do? When I go in to add a printer via Administration I don't know which option to choose and what settings to use.

Any help would be greatly appreciated.

---

### Post by cforput on 2011-03-14
Bump

---

### Post by walt.smith1960 on 2011-03-14
Do you know the printer/print server's I.P. address? if so, I've had success with manually editing the Device URI.  This is found by system -> administration ->printing -> right click on printer -> properties.   Right now you probably have usb://something. I would try changing that to socket://xxx.xxx.xxx.xxx:9100 where the xxx is the I.P. address. If you have a separate print server I'm not sure how to determine its I.P. address.   I assume you've tried "find network printer?"  I hope this is of some use to you.

---

