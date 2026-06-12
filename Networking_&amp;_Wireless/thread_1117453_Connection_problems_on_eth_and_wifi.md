---
title: "Connection problems on eth and wifi"
date: 2009-04-06
forum: Networking &amp; Wireless
---

### Post by Johnco on 2009-04-06
I have recently received a laptop, a Commodore KE8370MB, which I have formatted and installed Ubuntu 8.10.

Installation went fine except for video drivers (had to use VESA), however, I have found issues attempting to connect to the Internet.

Ubuntu recognized both the ethernet and the wi-fi devices and provided suitable drivers for them, as lspci has shown. Ubuntu can detect whenever the ethernet cable is connected / disconnected, and the wi-fi can list existing networks and their info. However, whenever I attempt to connect to any wireless or ethernet network I get a "can't connect error" after 30 seconds or so.

I tried running dhclient myself, and it states that no DHOFFER is received, but my desktop PC (also running Ubuntu) can connect using the exact same ethernet cable.

I'm not sure if the real issue is at dhcp, or maybe at a lower level, though if it was dhcp it would explain both ethernet and wi-fi failures.

Any help or ideas are welcome.

I haven't touched any configuration files since I've found nothing wrong while I examined the issue. I have also discarded any router issues, connecting the laptop directly to the provider with no results.

---

### Post by superprash2003 on 2009-04-06
try setting up static ip.. also try disabling ipv6 [http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html](http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html)

---

### Post by Johnco on 2009-04-11
No use, but thanks anyway.

For extra information, the wifi is a realtek 8187b, which is supported out of the box by ubuntu 8.10, as stated here under OPTION #2: [https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b#line-252](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b#line-252)

On it's behalf, the Ethernet driver installed is a VT6102 [Rhine-II] (rev 7c) by VIA Technologies.

Thanks for the help.

---

