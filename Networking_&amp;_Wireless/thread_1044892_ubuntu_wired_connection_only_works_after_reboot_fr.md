---
title: "ubuntu wired connection only works after reboot from vista"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by theromanone on 2009-01-19
Hi there, I have a Vista and Ubuntu 8.1 dual-boot.. seems my wired connection is only working when I reboot the computer from my Vista (while being connected by wire to the internet).

The problem is, if I log out and back into Ubuntu, my wired connection doesn't work anymore? Any tips?

my Ethernet card is "Realtek RTL8102E/8103E Family PCI-E Fast Ethernet NIC"

thanks!

---

### Post by Felliph3 on 2009-01-19
Have you tried clicking on the network icon up top and clicking on "wired" or "eth0" or "Auto eth"? Sometimes reconnecting the wired connection connects it. Ubuntu doesnt always automatically connect to wired.

---

### Post by cariboo on 2009-01-20
Open a Applications-->Accessories-->Terminal and type:

```
sudo dhclient eth0
```

To see if you can get an ip address.

Jim

---

### Post by theromanone on 2009-01-20
I will try getting the ip tomorrow, but dont think I would have one since I'm using my university's wired network (clean access agent is a must to even log onto network in windows)

Also for some reason I only can download at about a tenth of the speed as compared to vista (using firefox on ubuntu vs. chrome on vista)?

-so far, everything seems very much slower in ubuntu and do not see any advantages over vista, including simple file browsing.. maybe its my dual-boot?



System: Intel Core 2 Duo T5800 @ 2Ghz (64-bit system)
        4GB RAM

---

### Post by Iowan on 2009-01-20
I remember seeing another thread about that problem - apparently Windows (might have been XP) drivers remain active unless machine is rebooted.

---

### Post by theromanone on 2009-01-20
ok so i entered "sudo dhclient eth0"
got this: 

Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:23:8b:0d:f2:14
Sending on   LPF/eth0/00:23:8b:0d:f2:14
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

----------- these results were after I even shut off the laptop completely, took out battery, power cord, ethernet plug, and held the Power button to drain all excess power to the computer for 20 seconds.

I then waited until i saw the ubuntu screen and then plugged my ethernet cord back in and... nothing!


*More Info:

In Vista Device Manager, my advanced properties of the ethernet card (Driver Version 6.214.1211.2008) list:
Auto Disable PCle (Powersaving) DISABLED
Auto Disable PHY(Powersaving)   DISABLED
Flow Control                    ENABLED
Interrupt Moderation            ENABLED
IPv4 Checksum Offload           Rx & Tx ENABLED
Large Send Offload v2 (IPv4)    ENABLED
Large Send Offload v2 (IPv6)    ENABLED
Network Address                 Not Present
Priority & VLAN                 Priority & VLAN ENABLED
Receive Buffers                 512
Receive Side Scaling            ENABLED
Shutdown Wake-On-LAN            ENABLED
Speed & Duplex                  Auto Negotiation
TCP Checksum Offload (IPv4)     Rx & Tx ENABLED
TCP Checksum Offload (IPv6)     Rx & Tx ENABLED
Transmit Buffers                128
UDP Checksum Offload (IPv4)     Rx & Tx ENABLED
UDP Checksum Offload (IPv6)     Rx & Tx ENABLED
Wake-On-LAN Capabilities        Pattern Match & Magic Package
WOL & Shutdown Link Speed       10 Mbps First

--In Power Management, these boxes are UNCHECKED:
Allow the computer to turn off this device to save power
Allow this device to wake the computer
Only allow management stations to wake the computer

---

### Post by theromanone on 2009-01-21
healthy bump :).


update: the wired internet only works if I restart the computer from vista and duat boot into ubuntu.. but once I log out/restart ubuntu it will not be able to even connect to the wired internet..

---

