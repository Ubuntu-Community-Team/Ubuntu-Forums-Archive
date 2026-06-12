---
title: "[RT61] EW-7128g: No DHCPOFFERS received."
date: 2009-07-22
forum: Networking &amp; Wireless
---

### Post by vcppp_p on 2009-07-22
Hi,
 I'm trying to get my EW-7128g with RT61 oboard running on my PC. 
 The card is properly recognized (lspci says "01:0a.0 Network controller: RaLink RT2561/RT61 802.11g PCI"). Unfortunately, the default,built-in rt61pci driver not only gives incorrect signal level (it says it's only 57% of signal, while the antenna is about 3 feet from router), but also while trying to connect (using Wicd) it stays trying to receive the IP. Running "sudo dhclient wlan0" outputs 6 times "DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval [X]" where [X] varies from 2 to 21 so far. Unfortunately later it says "No DHCPOFFERS received. No working leases in persistent database - sleeping."

I tried bulding the latest drivers from RaLink Tech website, which I did. I put "rt61pci" on modprobe.d blacklist, then I installed self-built rt61.ko driver. It appeared on lsmod list instead of rt61pci, unfortunately - it didn't solved DHCPOFFERS problem. 

Then I tried ndiswrapper. I removed both native drivers (built-in and self-built) and installed driver for ndiswrapper, then modprobed it. Now, with ndiswrapper driver it gives me the correct signal level, BUT ... still can't connect - "No DHCPOFFERS..." :(

It's definitely not the fault of the router. I just connected to it with my Symbian-running phone (Nokia E61) and I had no problems using it. I checked the configuration of the phone, it uses DHCP for this connection so the router's DHCP server is rather running properly. 

The network is not encryped. It doesn't has any access controll based on MAC nor whatever. Literally NO LIMITATIONS.  

I've also checked the card - I've installed it on my second PC running XP. It connected to my network in two seconds ....

Please, help ... I'm not going to drop linux because of this card. I'm not going to buy a new one, as it is quite expensive in my country.

---

### Post by Iowan on 2009-07-23
I had a similar problem, but on [wired]("http://ubuntuforums.org/showthread.php?t=1156441").  Dunno if it'll help...

---

