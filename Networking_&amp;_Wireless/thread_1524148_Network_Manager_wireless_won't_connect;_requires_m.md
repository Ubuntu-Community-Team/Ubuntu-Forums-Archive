---
title: "Network Manager wireless won't connect; requires manual connection"
date: 2010-07-04
forum: Networking &amp; Wireless
---

### Post by sebastianrimbaud on 2010-07-04
I'm on a kubuntu 10.04 using a dlink dwa130 usb wireless thing.

I used wicd and the native network manager and none of them connect or detect the wireless connections.

I at first thought i needed to reinstall the dlink driver, but i tried the manual command

$ sudo iwlist wlan0 scan
$ sudo iwconfig eth1 essid "NETGEAR"
$ sudo dhclient wlan0

and that's the only method that works right now. However, it's not very convenient and it's the family computer. I'd like for the internet to connect automatically without the command-line to make it easy on them.

---

