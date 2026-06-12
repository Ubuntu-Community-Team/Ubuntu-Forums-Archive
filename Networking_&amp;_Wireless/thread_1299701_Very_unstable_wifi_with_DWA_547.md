---
title: "Very unstable wifi with DWA 547"
date: 2009-10-24
forum: Networking &amp; Wireless
---

### Post by petarv on 2009-10-24
Hi

I installed a fresh ubuntu on my desktop computer yesterday, but it seems not to fully support my wireless PCI card from Dlink. Model DWA 547.

Connection and transfer speed are very unstable, and almost impossible to use. I tried to install the XP drivers through the ndiswrapper, and after reboot I ended up with no wireless connection at all. :confused:

---

### Post by petarv on 2009-10-24
still in need of wireless connection in ubuntu :(

---

### Post by Sylslay on 2009-10-24
unstable for me sound lake mixed mode b/g on Yous router ?
If You habe one type wifi card, switch on router for that type. Only b, only g, only n. Router Dlink ...


"these cards and other Atheros 5478 chipset cards" 
this post help :about atheros ...
[http://ubuntuforums.org/showthread.php?t=1286503](http://ubuntuforums.org/showthread.php?t=1286503)

modprobe ath9k // driver for atheros Dlink - DWA series, but not sure is Yours supported?

[http://linuxwireless.org/en/users/Drivers/ath9k/devices](http://linuxwireless.org/en/users/Drivers/ath9k/devices)

---

### Post by petarv on 2009-10-25
Thank you, but it seems that I need to buy a new network card. Many owners of this card wrote about how it is unstable...

Perhaps I will go for ASUS WL-138g V2 PCI adapter. It seems to be supported "out of the box" by ubuntu and it seems that ubuntu users didn't have any major problems with it according to google.

---

### Post by calande on 2012-02-25
Jeez...It seems it's a NIC one has to stay away from...I almost purchased one, but I said to myself "let's see how well supported it is by Ubuntu". Thank God I read all these comments on this NIC! I still don't know which NIC to buy, I have my third NIC that doesn't work properly with my Ubuntu partition :(

---

