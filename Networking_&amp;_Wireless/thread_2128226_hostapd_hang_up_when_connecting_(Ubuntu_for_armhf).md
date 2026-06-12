---
title: "hostapd hang up when connecting (Ubuntu for armhf)"
date: 2013-03-22
forum: Networking &amp; Wireless
---

### Post by josephonthejob on 2013-03-22
Dear all,

I'm trying to setup an hot spot wifi from a board running ubuntu.

I've installed hostapd and udhcpd.

This is my /etc/hostapd/hostapd.conf

```
interface=wlan0
driver=nl80211
ssid=armSSID
auth_algs=1
channel=1
wpa=0
ignore_broadcast_ssid=0
```

This is my /etc/network/interfaces

```
auto lo
iface lo inet loopback

auto eth0
iface etho inet dhcp

iface wlan0 inet static
      address 192.168.2.1
      netmask 255.255.255.0

auto br0
iface br0 inet dhcp
bridge_ports eth0 wlan0
```

This si my /et/udhcp.conf (only the uncommented lines)

```
start           200.168.0.20    #default: 192.168.0.20
end             200.168.0.254   #default: 192.168.0.254
interface       wlan0           #default: eth0
remaining       yes             #default: yes
opt     dns     8.8.8.8  192.168.10.10
option  subnet  255.255.255.0
opt     router  192.168.10.2
opt     wins    192.168.10.10
```

everything seems to work (execpt not finding /dev/random ... brutally fixed with a ls) but when I connect my iPhone it can't receive the ip and can't go on internet.
This is what I have in console:

```
Using interface wlan0 with hwaddr de:ad:be:ef:00:00 and ssid 'armSSID'
wlan0: STA 00:88:65:8f:7a:d1 IEEE 802.11: authenticated
wlan0: STA 00:88:65:8f:7a:d1 IEEE 802.11: associated (aid 1)
wlan0: AP-STA-CONNECTED 00:88:65:8f:7a:d1
wlan0: STA 00:88:65:8f:7a:d1 RADIUS: starting accounting session 514C806D-00000000
```



have someone faced this problem?

---

