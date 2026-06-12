---
title: "DNS doesn't work on boot when WPA is used"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by FreeFull on 2008-12-20
Hello. I put my wireless settings in /etc/network/interfaces, but since I set up WPA, DNS doesn't work until I do 'iwconfig wlan1 essid Main key off && dhclient wlan1' as root. I can connect to IP addresses before I do that command. Here is my /etc/network/interfaces:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

allow-hotplug eth1

iface eth1 inet dhcp
## dhcp
# address 192.168.1.2
# netmask 255.255.255.0
# gateway 192.168.1.1
## static
# address 192.168.0.11
# netmask 255.255.255.0
# gateway 192.168.0.1


auto wlan1
iface wlan1 inet dhcp
wpa-driver wext
wpa-conf /etc/wpa_supplicant.conf
wireless-essid		Main
wireless-mode		managed
# auto eth1

```
eth1 is my wired interface. As a temporary solution, I made a script with 'iwconfig wlan1 essid Main key off && dhclient wlan1' and made an activator on my panel that executes the script with gksu.

---

### Post by FreeFull on 2008-12-22
Bump

---

