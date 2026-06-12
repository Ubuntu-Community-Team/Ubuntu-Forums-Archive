---
title: "AcerAspireOne(AR5007EG) ubuntu-ubuntu ad hoc connection"
date: 2009-04-25
forum: Networking &amp; Wireless
---

### Post by famer on 2009-04-25
Hey! I just trying to get ad hoc between my aspire one ubuntu with AR5007EG wireless card and my PC with d-link dwa-110 usb adapter.
What's intresting is that PC's ubuntu and acer one windows client ad-hoc works fine. Between acer one ubuntu(ubuntu netbook remix) and windows PC ad-hoc works fine.
But ubuntu - ubuntu didn't work. Aspire one just periodically asking for wifi wep key while trying to connect...
On my PC i'm using /etc/network/interfaces and ndiswrapper driver(just with 11Mb bitrate, may be this is a problem):

auto lo
iface lo inet loopback

auto eth2
iface eth2 inet dhcp

auto wlan0
iface wlan0 inet static
wireless-key 1234567890
wireless-channel 6
wireless-mode ad-hoc
wireless-essid famer-desk
address 192.168.0.1
netmask 255.255.255.0

On acer aspire one i'm using ubuntu netbook remix and standart network manager.
As i sad, it normally connects to win network, and his win client normally connects to above pc's ubuntu network.

Sorry for bad english :(

---

