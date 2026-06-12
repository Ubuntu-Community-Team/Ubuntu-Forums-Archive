---
title: "Wireless ICS cutting out"
date: 2010-02-09
forum: Networking &amp; Wireless
---

### Post by andou on 2010-02-09
I'm using Ubuntu 9.10 64 bit

I followed this [InternetConnectionSharing]("https://help.ubuntu.com/community/Internet/ConnectionSharing") guide, but made a couple of changes to share through my wireless adapter.

It works well, except that the Internet connection seems to cut out every few minutes on my laptop while connected through this wireless connection.

Here's my /etc/network/interfaces if that helps:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet static
        wireless-key 1234567890
        wireless-channel 6
        wireless-mode ad-hoc
        wireless-essid 'Wireless Connection'
        address 192.168.0.2
        gateway 192.168.0.1
        netmask 255.255.255.0

```

---

