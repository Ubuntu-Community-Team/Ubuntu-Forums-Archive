---
title: "Wireless Connection Drops"
date: 2010-11-17
forum: Networking &amp; Wireless
---

### Post by cdusseau on 2010-11-17
I have a small server setup as a dhcp server on eth0. I also have a wireless connection wlan0. I use the following interfaces files:


```
auto lo
iface lo inet loopback

auto eth0 wlan0
iface eth0 inet static
	address		101.101.101.101
	netmask		255.255.255.0
	network		101.101.101.0
	broadcast	101.101.101.255
	gateway		101.101.101.101

iface wlan0 inet dhcp
	wireless-essid	<ssid>
	wireless-key	<key>
```

Where I obviously have ssid and key filled in.

My issue is that I need to start the connection manually via /etc/init.d/networking restart. I have to do this when I boot the machine and also occasionally the connection fails and I have to restart it.

I am just wondering if there is a setting I am missing or if there's a way to automatically restart the connection if it fails  without resetting eth0 as well.

---

