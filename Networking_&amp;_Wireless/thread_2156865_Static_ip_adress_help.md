---
title: "Static ip adress help"
date: 2013-06-23
forum: Networking &amp; Wireless
---

### Post by kirby2ig on 2013-06-23
Okay, so I was following the instructions seen here [http://freeyourit.fitguru.biz/2013/05/linux-for-newbs-setting-static-ip.html](http://freeyourit.fitguru.biz/2013/05/linux-for-newbs-setting-static-ip.html) to set up a static ip adress on a wifi network. I opened up the /etc/network/interfaces file only to find that there was no entry for wlan0. Also, when I run ifdown, I get this: 
$ sudo ifdown wlan0
ifdown: interface wlan0 not configured.
 Although it says that is isn't configured, my wireless still works and ifconfig tells me that wlan0 is running and has an ip adress. Any ideas on how to fix this?

---

### Post by steeldriver on 2013-06-23
Unfortunately that's a hazard of following random instructions on the web

Assuming you are using a Desktop (not Server) version of Ubuntu, the network connections are managed by the Network Manager service - that's separate from the old networking service that uses /etc/network/interfaces and ifup & ifdown, and it ignores anything defined there unless forced to 'manage' it

If you want a static LAN IP in Network Manager, you do it via the desktop applet (or equivalently by firing up nm-connection-editor), selecting the connection you want to edit, and changing 'Method' from DHCP to 'Manual' in the IPv4 settings tab - then fill in the IP fields as appropriate

---

### Post by SeijiSensei on 2013-06-23
Another option might be to use a "MAC reservation" on your router to assign your computer's wifi card a static IP.  Then you could revert to using DHCP, but you will get the same address every time.

---

### Post by kirby2ig on 2013-06-23
Thanks [COLOR=#000000]steeldriver, it works![/COLOR]

---

### Post by steeldriver on 2013-06-23
You're welcome - but please do consider doing it the way suggested by SeijiSensei if your router supports it - it keeps everything 'centralized' and avoids the possibility of address conflicts

At the very least, make sure that the address that you used is outside the router's DHCP address pool so it doesn't try to assign the same address to another device

---

### Post by SeijiSensei on 2013-06-23
Keeping it outside the pool is obviously the right approach.  However the ISC dhcp server first pings to see if an address is already in use before it tries to give it another host.  Who knows whether commercial home routers use such techniques, though it seems a simple and obvious solution to the problem of inadvertently assigning duplicate addresses.

---

