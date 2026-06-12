---
title: "wlan active but can't ping anything"
date: 2012-12-19
forum: Networking &amp; Wireless
---

### Post by leargaf on 2012-12-19
Hi,

I installed a PCI wireless card in my PC to connect to a 3G wireless router. The network connection was setup fine and wlan0 shows up as active but it's not working. I can see my PC in the DHCP list of the router (from a different PC) but I can't even ping the router from my PC. I get the following connection information:
General
Interface: 802.11 WiFi (wlan0)
Driver: rt2800pci
Security: WPA/WPA2

IPv4
IP address: 192.168.0.101
Broadcast address: 192.168.0.255
Subnet mask: 255.255.255.0
Default route: 192.168.0.1

route -n
0.0.0.0     192.168.0.1 0.0.0.0       UG 0    0 0 wlan0
169.254.0.0 0.0.0.0     255.255.0.0   U  1000 0 0 wlan0
192.168.0.0 0.0.0.0     255.255.255.0 U  2    0 0 wlan0

dmesg | grep wlan
wlan0: authenticated
wlan0: associated
ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

ping 192.168.0.1
0 received

ping 192.168.0.100
0 received

I appreciate your help.

---

