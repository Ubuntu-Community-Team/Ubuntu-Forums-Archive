---
title: "netgear Wlan"
date: 2006-03-12
forum: Networking &amp; Wireless
---

### Post by Tobitas on 2006-03-12
installed ubuntu on my old toshiba laptop. I only have a netgear MA521 Wlan device connected via PCMCIA.

According to many available guides on the web I installed the drivers from netgear with ndiswrapper. Typing ndiswrapper -l gives me "ma521nd5   driver present, hardware present"

typing iwconfig gives me: 
"wlan0 ieee802.11b ESSID: off/any 
mode auto frequency 2,412 Ghz, access point: 00:00:00:00:00:00: ..."

ifconfig gives me: "wlan0 link encap: ethernet hwaddr 00:09:5B:8B:0C:6B
inet6 addr: fe80::209:.......etc."

I configured the device in System-administration-networking. The device shows up and is marked as active. I provided ESSID and WEP key (128 bit) there. 

still I have no internet connection. Also, I cannot ping my router. 
What do I do wrong? Please help me, this is driving me nuts.

Tobias

edit: router is set to dhcp, works well with suse on my other machine. network settings in ubuntu are also set to dhcp

---

