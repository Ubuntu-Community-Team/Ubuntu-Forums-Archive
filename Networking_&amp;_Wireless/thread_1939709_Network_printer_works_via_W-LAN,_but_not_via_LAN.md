---
title: "Network printer works via W-LAN, but not via LAN"
date: 2012-03-12
forum: Networking &amp; Wireless
---

### Post by chris011 on 2012-03-12
Hello,

I have the following problem: My network printer, a Kyocera FSC5100-DN is directly connected with a Motorola Netopia WLAN Router. Via D-LAN, 2 further access points are connected to the router. Additionally, one computer with Ubuntu 11.10 is directly connected to the Netopia router. Now, the following problem occurs:

I have given the network printer a static IP (192.168.1.33), so DHCP is switched off. With this configuration, all computers, which are connected via D-LAN or W-LAN to the rounter, can ping the printer and also print without problems. Only the computer, which is directly connected with the Netopia Router cannot ping the printer via [http://192.168.1.33](http://192.168.1.33) and so also not print. If I do now switch on DHCP, the computer with Ubuntu 11.10, connected directly to the Netopia router, prints without problems - but obviously, all other computers, adressing the printer via W-LAN or D-LAN cannot print anymore as the IP changes (although the IP range for DHCP was limited in the router, starting from 192.168.1.33 and ending at 192.168.1.33). 

Does someone have a way to solve that? I guess the way to fix the IP of the printer is straightforward, but somehow, then the router does not let the computer directly connected to the router adress the printer....

Thanks!

---

