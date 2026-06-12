---
title: "Problem with configuring Eth0"
date: 2010-11-16
forum: Networking &amp; Wireless
---

### Post by Alphamonkey on 2010-11-16
Hi, I just installed the latest version of ubuntu which i just downloaded yesterday. I installed it from the live cd. My problem is that it will not connect to the internet through eth0. I noticed the problem on the live cd but didn't really give it consideration before installing. I know that the NIC works because i have a live cd of mint and have slax and knoppix on my usb drive and the internet works fine with those without any extra configuration. I have tried to configure eth0 to use dhcp and i have also tried manual configuration but i can't get it to work. I am thinking it may be a driver issue but i don't know how to check and i have never had a driver issue with eth0 and linux before.

---

### Post by dineshs on 2010-11-17
Please post the results of```
sudo dhclient eth0
```and```
sudo lshw -C network
```

---

### Post by Alphamonkey on 2010-11-17
Hi thanks for the response I actually got it to work. I just created a new connection under the edit connections and set everything up as automatic. However auto eth0 (whats supposed to be my default) still doesn't work so after a reboot i have to change it to the new connection again. Not a big issue but still an inconvenience. If it helps here is the info you asked for.

Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:19:d1:00:36:41
Sending on   LPF/eth0/00:19:d1:00:36:41
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.1.6 from 192.168.1.1
DHCPREQUEST of 192.168.1.6 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.6 from 192.168.1.1
bound to 192.168.1.6 -- renewal in 32729 seconds.

  *-network               
       description: Ethernet interface
       product: 82566DC Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:19:d1:00:36:41
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k4 duplex=full firmware=1.1-0 ip=192.168.1.6 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:46 memory:93200000-9321ffff memory:93224000-93224fff ioport:30c0(size=32)

again i appreciate the response and its not a huge issue but i would like to know how to change my new connection to default and/or know why the other one didn't work "out of the box." Thank you.

---

