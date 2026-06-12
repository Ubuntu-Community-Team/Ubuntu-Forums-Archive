---
title: "Internet does not always automaticly connect on boot"
date: 2011-03-11
forum: Networking &amp; Wireless
---

### Post by Screatch on 2011-03-11
Chipset: Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 02)
Router: Thomson TG585v7
Version: Linux Mint 10 Julia, clean install, all updates installed (Ubuntu 10.10)
Connected through ADSL.

I  have a very strange problem, sometimes, when i turn my computer on, it  doesn't always connects to internet, this happens very randomly.  Sometimes it can take up to 4 reboots to get internet up and running,  sometimes its working from the first boot, i figured it has something to  do with dhcp.

That's very annoying. The interesting thing is  that this didn't happen before. It's just, one day this problem appeared  so probably something to do with updates.
I was unable to reproduce this problem on my Linux Mint 10 netbook, on Windows 7 on same PC, or other PCs in my apartment.

I just reinstalled Mint yesterday, just to check if this problem will go away, but unfortunately, problem still persists.

Logs:

Log from messages
```
Mar  8 18:37:36 vitali-desktop kernel: [    0.013966] Initializing cgroup subsys net_cls
Mar  8 18:37:36 vitali-desktop kernel: [    0.405979] audit: initializing netlink socket (disabled)
Mar  8 19:29:31 vitali-desktop kernel: [    0.013973] Initializing cgroup subsys net_cls
Mar  8 19:29:31 vitali-desktop kernel: [    0.405977] audit: initializing netlink socket (disabled)
Mar  8 19:36:18 vitali-desktop kernel: [    0.013982] Initializing cgroup subsys net_cls
Mar  8 19:36:18 vitali-desktop kernel: [    0.415912] audit: initializing netlink socket (disabled)
```Output from sudo dhclient
```
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:19:d1:80:54:41
Sending on   LPF/eth0/00:19:d1:80:54:41
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```Output from ip addr show
```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:19:d1:80:54:41 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::219:d1ff:fe80:5441/64 scope link 
       valid_lft forever preferred_lft forever
```Output from sudo lshw -C network

```
  *-network               
       description: Ethernet interface
       product: 82566DC Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:19:d1:80:54:41
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=e1000e  driverversion=1.0.2-k4 duplex=full firmware=1.1-0 latency=0 link=yes  multicast=yes port=twisted pair speed=100MB/s
       resources: irq:46 memory:e3200000-e321ffff memory:e3224000-e3224fff ioport:30c0(size=32)
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
```Although the problem is on Mint, i still see a point in writing here because Mint is pretty much the same Ubuntu.

Please tell me what more information do you need.

I'd apprectiate any help on this matter. Thank you in advance.

---

### Post by Screatch on 2011-03-11
Um, um, erm, up.
Some help is much appreciated.

---

### Post by Screatch on 2011-03-13
Oh come on guys, pleeease :) Some help is much appreciated.

---

### Post by Perfect Storm on 2011-03-13
Hi Screatch

There's a Linux Mint forum to get help with your distro.
You'll find it here: [http://forums.linuxmint.com/](http://forums.linuxmint.com/)


regards
A.I. Dude
Ubuntu Forum Staff

---

