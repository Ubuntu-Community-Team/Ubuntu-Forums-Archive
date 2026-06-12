---
title: "network manager, wpa_supplicant etc"
date: 2009-12-17
forum: Networking &amp; Wireless
---

### Post by bender1234 on 2009-12-17
Hey

I'm setting up a server-mediacenter-dhcpserver-nat-sambaserver-etc on karmic 9.10 x64.

I do not like the network manager in ubuntu for several reasons, and I want my system to start all services at bootup, that is before login.

The box runs on two nets, one beeing wifi connected to a router which it gets a static ip from. The other subnet it acts as a dhcp server with a NAT with a static ip.

After tons of googling I'm a bit fuzzed over all the solutions, and I'm wondering which is the best to use. ATM I use network manager for the wifi, which works well. But it seems to don't read etc/network/interfaces, where I've configured my ethernet stuff. I have to do a etc/init.d/networking restart in order to get eth0 up.

I really do want everything configured in interfaces, which solution is the best to go for getting wifi up here. wpa_supplicant? ndiswrapper? I'm using WPA-PSK.

Finally. After I sat up the two nets, samba shares will not show browsing the workgroup. It worked well when only running on wifi. Any pointers here? It works when entering either of its ip's. DHCP is configured to not give out adresses to the WiFi subnet, and I'm sure that it is correctly setup.

cheers,
Bender

---

