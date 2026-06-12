---
title: "How do I configure Dial up in 11.10 using SmartPCI56 modem"
date: 2011-12-13
forum: Networking &amp; Wireless
---

### Post by bwallum on 2011-12-13
Yes indeed, I want to dial up in this day and age using Oneiric.

sudo lspci returns:-
:
03:05.0 Modem: Philips Semiconductors SmartPCI56(UCB1500) 56K Modem (rev 01)
:
so the modem can be identified.

scanModem confirmed the id with 

 PCI slot    PCI ID        SubsystemID    Name
 ----------    ---------    ---------    --------------
 03:05.0    1131:3400    1436:4001    Modem: Philips Semiconductors SmartPCI56

I have downloaded the packages sl-modem-source and sl-modem-daemon from synaptic.

However there seems to be quite a lot more involved. I have downloaded module-assistant and tried to install using it but no joy, it simply says failed to build with a short and unhelpful log file.

All HowTos that I have come across are quite old and I'm getting quite lost trying many different things.

Any help would be appreciated. Have you installed a dial up modem in Oneiric?

---

### Post by jerrrys on 2011-12-15
I do not use dial up, but got some oneiric hits here:

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=configure+Dial+up+in+11.10+oneiric&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=configure+Dial+up+in+11.10+oneiric&as_qdr=all&sa=Google+Search&lang=en)

goodluck

---

### Post by bwallum on 2011-12-26
Thanks for you help. After a couple of weeks trying I fired up XP which linked immediately. Oh hum..

---

