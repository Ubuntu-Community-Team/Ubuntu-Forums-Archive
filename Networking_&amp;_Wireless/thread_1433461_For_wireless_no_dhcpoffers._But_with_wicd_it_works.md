---
title: "For wireless: no dhcpoffers. But with wicd it works"
date: 2010-03-19
forum: Networking &amp; Wireless
---

### Post by silencej on 2010-03-19
I am a command-line fan, and i came across the "no dhcpoffers received" problem. But when i turned to Wicd, my wireless worked with the same essid and WEP key. What tricks did the Wicd may play in addition to my commands to make my wireless work?

Here is my script:
```
sudo ifconfig eth0 down
sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig <interface> up
sudo iwconfig wlan0 essid "******"
sudo iwconfig wlan0 key **********
sudo iwconfig wlan0 key open
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

```And the output
```
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/**:**:**:**:**:**
Sending on   LPF/wlan0/**:**:**:**:**:**
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```While with wicd the wireless works fine.

BWT, iwlist can't find a key after i suppley wlan0 the WEP, even when my wireless is working:
```
sudo iwlist wlan0 keys
[sudo] password for USERNAME: 
wlan0     0 keys available :
          Current Transmit Key: [1]

```


So where should i start to debug my commands? And what tricks wicd may do?

---

### Post by silencej on 2010-03-19
Ok, problem solved. The situation is, my wireless LAN has multiple APs with a same essid. So i need to manually specify a channel.
So if you come across a situation like mine, try adding a line:
```
sudo iwconfig wlan0 channel *
```

However, I still can't figure out why iwlist can't list my keys.

---

