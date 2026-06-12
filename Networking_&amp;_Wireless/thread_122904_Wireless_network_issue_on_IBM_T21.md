---
title: "Wireless network issue on IBM T21"
date: 2006-01-28
forum: Networking &amp; Wireless
---

### Post by new-to-ubuntu on 2006-01-28
I loaded Ubuntu 5.10 on an IBM T21 lap top and all is well...except for problems with wireless connection. 

Details are:

wireless card, Network Enywhere (Linksys) NWP11B, Network Everywhere router - card and router works fine with another XP loaded laptop.

I've installed the driver thru the wireless driver installer GUI tool. Hardware and software is detected. IWconfig reports details on driver, except there is no IP address assigned to the PCMCIA card. How can I force it?

Tried disabling WEP, did some fine confused editing of interfaces file, and finally baulked at rebuilding the kernal and things like that, based on google directions (e.g. houseofcraig.net).

Please point me in the right direction.:confused: :-k :-?

---

### Post by new-to-ubuntu on 2006-01-29
Wireless connection works fine now. I re-installed Ubuntu with the card in the PCMCIA slot, chose the wireless option instead of wired LAN during configuration. Card was auto detected and works well now.

BTW, it is a T23 laptop. The NWP11B card has the ACX100 chipset.

---

