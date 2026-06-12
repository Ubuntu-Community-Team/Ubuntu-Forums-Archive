---
title: "Wireless access point with local access, no dhcp, how?"
date: 2010-02-09
forum: Networking &amp; Wireless
---

### Post by TsUPeR on 2010-02-09
I have found tremendous amounts of information in this forum but nothing helping me solving my problem.
I got a Zotac Ionitx-a running netbook remix 9.10. Its currently connected by wire (eth0) to my router(dhcp). What I'd like to achieve is a wireless access point without dhcp (provided by my router) and with local connectivity (running xbmc).
So far I have spent hours searching and trying and got all parts running but not together.
* For the wireless access part I have installed hostapd and got this working (can connect but don't get IP)(interface=wlan0 bridge=br0)
* For bridging I have installed bridge-utils and with some set up managed to get it partially working (local access).
* I have enabled packet forwarding (/etc/sysctl.conf)
* I have messed around in /etc/network/interfaces but are unsure what to do to get my setup working. This is my current (not working) test
```

auto lo
iface lo inet loopback
#auto eth0
#iface eth0 inet dhcp
#auto wlan0
#iface wlan0 inet manual
# wireless-mode master
auto br0
iface br0 inet dhcp
 bridge-ports eht0 wlan0
 bridge-fd 0
 bridge-maxwait 0

```
 With this setup hostapd is up and I can connect but don't get IP. Localy I can not access anything. I have commented out some of the options I have un-successfully tested.
What am I missing here? Is hostapd doing some automagic Im missing? All help appreciated.

---

### Post by TsUPeR on 2010-02-10
Did some more testing and managed to get a connection using this set.up

```
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet manual
auto br0
iface br0 inet dhcp
 bridge-ports eht0 wlan0
 bridge-fd 0
 bridge-maxwait 0
```

However I can only connect with one client at a time...
Just found this [http://bigbrovar.wordpress.com/2009/01/17/share-you-internet-wirelessly-on-ubuntu/](http://bigbrovar.wordpress.com/2009/01/17/share-you-internet-wirelessly-on-ubuntu/) and it could make things a whole bit easier..

---

