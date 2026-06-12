---
title: "VPN interface MTU size"
date: 2010-02-20
forum: Networking &amp; Wireless
---

### Post by d1brian on 2010-02-20
For learning purposes i've set up a vpn between a laptop (running ubuntu) and a pc (running windows). The 2 computers are on the same lan. The VPN server is set on the laptop, and as a guide i used this tutorial: [http://ubuntuforums.org/showthread.php?t=1064776](http://ubuntuforums.org/showthread.php?t=1064776)

The problem is that the mtu on the ppp0 interface is 1396 and the mtu on the eth0 interface is 1492 so in order to pass packets from the et0 if to the ppp0 if, the laptop needs to fragment the packets, and here is where the problem appears: the packets come with the don't fragment bit set. I've tried lowering the mtu of the eth0 if but that didn't work. The only way i managed to make this work is setting the ppp0 mtu size to 1492. The thing is that setting the mtu and mru in the pptpd-options file to 1492 doesn't do anything (at least to solve this problem) and the only way to set the mtu of the ppp0 if is to manually set it using: ```
sudo ifconfig ppp0 mtu 1492
``` The issue with this is that every time the connection resets i have to enter the command. 

Is there a way to automatically set the mtu of the ppp0 if?

Thanks in advance.

---

### Post by zaphod777 on 2010-02-20
You shouldn't be connecting to a VPN server from the same LAN segment it will cause problems since the source and destination network are both on the same "network" being 192.168.1.x or something similar. Your computer doesn't know weather to go through the regular LAN connection or through the PPTP connection. 

Try port forwarding from your router and connecting from another network like an open WIFI hotpot. 

From the outside the other internet routers will automatically change the MTU and fragment the packets except in the rare case of "black hole routers" 

[http://support.microsoft.com/kb/314825](http://support.microsoft.com/kb/314825)

it's a Microsoft article but the same principle applies.

---

### Post by d1brian on 2010-02-22
Connecting to the vpn server from another location works. Still, isn't there a way to make the virtual interface have a different mtu size?

---

