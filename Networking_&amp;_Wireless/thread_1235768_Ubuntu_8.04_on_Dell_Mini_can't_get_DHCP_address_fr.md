---
title: "Ubuntu 8.04 on Dell Mini can't get DHCP address from Apple Airport Extreme"
date: 2009-08-09
forum: Networking &amp; Wireless
---

### Post by michael.new on 2009-08-09
I've checked through the forums and didn't see any thread that offered a solution to my problem so I'm posting here. If I missed a complete thread, please point me to it.

I just bought a new Dell Mini 10 that came with Ubuntu 8.04 preloaded.  I've been trying for the better part of a week to get it to connect to my home wireless network but no luck.  My home network is based around an Apple Airport Extreme (the one that looks like a white UFO) running in 8.011b/g compatibility mode.  I'm running a WEP 128 password and using DHCP+NAT to share a single, static IP address among my home machines (until now, they've all been Macs). The addresses are from the 10.0.1.x address space.

 I've been able to get the Dell to connect to the network but it cannot seem to get a DHCP address from the Airport. When I run [FONT="Courier New"]dhclient[/FONT]  I get the following output:

[FONT="Courier New"]
Listening on     LPF/eth1/00:25:56:77:de:8b
Sending on       LPF/eth1/00:25:56:77:de:8b
Sending on       Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

[/FONT]

At this point, I could really use some help.  Thanks!!

Michael

---

