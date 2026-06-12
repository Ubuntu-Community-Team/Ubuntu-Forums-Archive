---
title: "realtek 8187 on 9.10"
date: 2009-12-13
forum: Networking &amp; Wireless
---

### Post by AlexCunha on 2009-12-13
Hello,

One off my notebook haves a realtek 8187 wifi card (maybe B version) and I have also a USB external high perfomance wifi dongle with realtek 8187 (maybe L version).

I'm experimenting severall issues with this wifi cards.

The internal sometimes one doest get signal on places when other wifi cards (from other notebooks or even USB) get signal, sometimes around 40%, but working very well.

The wifi dongle (the high perfomance) doest get signal on places on a machine with <other operating system> with this dongle gets signal arround 30% / 70%. 
On same rare cases when I got signal, the connections to the network doest work (however, the other machine with <other operating system> works very well!!!).

So, what is the trouble with this chipset and Ubunru 9.10?
Is this chipset properly supported / included on the 9.10?
Do I need use ndiswrspper tricks?

Thanks for your help.

---

### Post by AlexCunha on 2009-12-13
lsusb

Bus 001 Device 009: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 001 Device 007: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter

uname -r
2.6.31-16-generic


Is the same type of problem I see reported where: [http://swiss.ubuntuforums.org/showthread.php?t=1314586](http://swiss.ubuntuforums.org/showthread.php?t=1314586)
And the same type of dongle.

---

