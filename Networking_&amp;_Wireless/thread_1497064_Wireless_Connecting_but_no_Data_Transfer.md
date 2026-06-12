---
title: "Wireless Connecting but no Data Transfer"
date: 2010-05-30
forum: Networking &amp; Wireless
---

### Post by itsonlybarney on 2010-05-30
I recently did a clean install of Ubuntu 10.04 and tried using a DLink DWL-G122 dongle for a wireless connection.

It seems to connect to the wireless router, but I cannot seem to access any websites using the wireless connection.  Ethernet connections to the computer work perfectly, but ethernet isn't ideal.

The results of the [FONT=Courier New]lsusb[/FONT] command is:
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 08bb:2902 Texas Instruments Japan 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 2001:3c00 D-Link Corp. [hex] DWL-G122 802.11g rev. B1 [ralink]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

I've tried solutions I've seen here on the forums, without success. 
[This one]("http://ubuntuforums.org/showthread.php?t=1468305") being one of them.

Any help would be appreciated.

---

### Post by Mortesins93 on 2010-07-08
I have the same problem

---

### Post by frankvw on 2010-07-08
In my experience, these symptoms generally indicate either,
a.) a WiFi authentication error (read: WEP/WPA/WPA2 password incorrect or omitted), or
b.) no DHCP address handed out by the WiFi AP, router or whatever on the LAN is supposed to take care of this. An 'ifconfig -a' should tell you whether or not you have a network interface corresponding with your WiFi card, and whether or not it has an IP address assigned to it.

So if it were me, I'd start there. :-)

// FvW

---

### Post by Mortesins93 on 2010-07-16
I managed to solve the problem. Thank you Frankvw. I disinstalled Xubuntu and installed it again and the i just added a DHCP client ID in the IPv4 options.

---

