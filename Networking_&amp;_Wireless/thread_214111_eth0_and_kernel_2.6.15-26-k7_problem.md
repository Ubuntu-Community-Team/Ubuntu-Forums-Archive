---
title: "eth0 and kernel 2.6.15-26-k7 problem"
date: 2006-07-12
forum: Networking &amp; Wireless
---

### Post by Animalus on 2006-07-12
**kernel 2.6.15-25-k7** (god)

dmesg | grep eth
[17179592.552000] eth0: VIA Rhine II at 0x1d400, 00:03:0d:0e:8d:78, IRQ 3.
[17179592.552000] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
[17179593.444000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17179609.432000] eth0: no IPv6 routers present 

**2.6.15-26-k7** (bad)

dmesg | grep eth [17179592.460000] eth0: VIA Rhine II at 0x1d400, 00:03:0d:0e:8d:78, IRQ 3.
[17179592.460000] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
[17179593.056000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17179634.604000] eth0: no IPv6 routers present
[17179637.344000] NETDEV WATCHDOG: eth0: transmit timed out
[17179637.344000] eth0: Transmit timed out, status 0003, PHY status 786d, resetting...
[17179637.344000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1

Configuration is good, several cases checked. It fails to collect parameters DHCP. It don't give manual setups too effect. In bug kernel 2.6.15-26-k7?

---

### Post by mips on 2006-07-12
Disable IPv6

---

### Post by Animalus on 2006-07-12
File:/etc/modprobe.d/aliases

alias net-pf-10 ipv6 off 
alias net-pf-10 off 
alias ipv6 off 
#alias net-pf-10 ipv6


... no efect...

kernel 2.6.15-25-k7 eth0 working very good

kernel 2.6.15-26-k7 eth0 bad bad bad :-k

---

### Post by Animalus on 2006-07-13
> /etc/init.d/networking restart
 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:03:0d:0e:8d:78
Sending on   LPF/eth0/00:03:0d:0e:8d:78
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 10.0.0.2 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:03:0d:0e:8d:78
Sending on   LPF/eth0/00:03:0d:0e:8d:78
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


No help my ?

---

### Post by mips on 2006-07-13
Do a search for that kernel version, I'm pretty sure I saw someone else complaining that it screwed it their networking.

File a bug report and stick to the older kernel for now until you find a solution.

---

### Post by Animalus on 2006-07-13
a'im reporting this bug...

---

