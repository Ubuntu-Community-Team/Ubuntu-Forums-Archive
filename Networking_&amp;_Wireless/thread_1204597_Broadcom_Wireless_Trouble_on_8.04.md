---
title: "Broadcom Wireless Trouble on 8.04"
date: 2009-07-04
forum: Networking &amp; Wireless
---

### Post by NeoZiggy on 2009-07-04
Hello all, happy 4th of July to all my fellow Americans out there, and good day/night to everyone else on our great planet.

I am using a "HP WLAN 54g W450 Network Adapter", according to WindowsXP, internal wireless card on a HP Pavilion ze5300 laptop. I just installed Ubuntu 8.04 from a CD I previously burned. I can not connect to wireless.

Let this be known:
1) I live in an apartment community that provides free wireless internet to its residents. I do not have access to the router or a wired connection.
2) When booted in to Ubuntu, I will not be able to download (apt-get) anything since the wireless doesn't work.
3) I do not have any blank CDs... or I'd burn 9.04 already.
4) Windows and Ubuntu are on the same HD, I can download files over Windows, save them to the hard drive then access them on Ubuntu.
5) I haven't used Ubuntu in a while.  :(

Ubuntu tells me I have a "Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02). National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller"

Here is a print out that could help you help me:
```

*-network:0
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64 module=ssb

*-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0b:cd:8b:a6:bd
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=natsemi driverversion=2.1 latency=90 maxlatency=52 mingnt=11 module=natsemi multicast=yes

*-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0b:cd:56:69:aa
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

zig@zig-box2:~$ sudo ifconfig wlan0 down
zig@zig-box2:~$ sudo dhclient -r wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/
wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:0b:cd:56:69:aa
Sending on   LPF/wlan0/00:0b:cd:56:69:aa
Sending on   Socket/fallback

zig@zig-box2:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: No such file or directory

```

Please let me know in detail what/where to download driver(s) I may need, and how to install them. Remember, I will have to download them over windows (saving your instructions to a text file) and then reboot to Ubuntu to do the rest.

Thank you!

---

### Post by NeoZiggy on 2009-07-05
Well, I installed 'ndiswrapper' and the closest windows driver I could find... that appears to be working, but it won't connect to the network. Its a non-secure network who's SSID is "needs password". What can I say, its a small apartment complex, they aren't too bright. Anyway, any help would be appreciated here.

---

