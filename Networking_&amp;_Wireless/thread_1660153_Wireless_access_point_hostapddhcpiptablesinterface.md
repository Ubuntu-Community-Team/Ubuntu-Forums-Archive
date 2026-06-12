---
title: "Wireless access point: hostapd/dhcp/iptables/interfaces"
date: 2011-01-05
forum: Networking &amp; Wireless
---

### Post by potat on 2011-01-05
Hi folks,

I am having some trouble getting my wireless access point server up and running. I have hostapd and the DHCP server working such that a device can connect to the network and is assigned an IP on 192.168.5.*. All network traffic works on this subnet.

The server is connected to the Internet via the secured ethernet at my university. I want to be able to access the Internet on the devices connected to the WAP (my laptop, for example). What is the best way to go about doing this? I have read about using brctl but I don't know if it is capable of spanning different subnets.

My /etc/network/interfaces:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
    pre-up wpa_supplicant -Dwired -ieth0 c/etc/wpa_supplicant/wired.conf -B
    post-down killall -q wpa_supplicant
    pre-up /usr/sbin/ethtool -s eth0 speed 100 duplex full autoneg off

iface wlan0 inet static
    post-up ifconfig wlan0 192.168.5.1

```

Though as a workaround I am running
```

ifconfig wlan0 192.168.5.1
/etc/init.d/dhcp3-server restart

```
in rc.local (the DHCP server was failing to start before the wireless card had the proper IP).

Any help would be greatly appreciated. Also please tell me if I'm doing something stupid in my configuration; networking is still very hazy to me. Thanks!

EDIT: My dhcpd.conf entry:
```

subnet 192.168.5.0 netmask 255.255.255.0 {
  range 192.168.5.10 192.168.5.49;
  option ip-forwarding off;
  option subnet-mask 255.255.255.0;
  option broadcast-address 192.168.5.255;

```

---

### Post by potat on 2011-01-05
Bump. Maybe posting this at 1:30AM wasn't such a great idea.

---

