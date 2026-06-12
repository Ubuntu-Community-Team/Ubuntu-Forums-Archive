---
title: "Trying to fix ethernet driver issue in 10.04"
date: 2012-02-18
forum: Networking &amp; Wireless
---

### Post by afanasiew on 2012-02-18
I have a wired pc running Ubuntu 10.04 (no partitions) and a wireless laptop with Windows XP. Lost internet on the pc only following an auto-update, discovered via forums it was an ethernet driver issue, so downloaded the recommended replacement from Realtek and followed the readme instructions as far as I could. No good.
Then tried setting a static IP address as per [http://www.jonathanmoeller.com/screed/?p=1669](http://www.jonathanmoeller.com/screed/?p=1669)
Still no good. I feel I must be close to a resolution, but need a helping hand. Please.
 
Afanasiew

---

### Post by Iowan on 2012-02-18
I'm really horrible with driver problems (need lessons from **chili555** ;) ).
What are results of **sudo lshw -C network** and **ifconfig -a** ?

---

### Post by afanasiew on 2012-02-19
Thanks for the response, Iowan.
 
I should have added that it's the 64 bit version.
 
```
*-network               
description: Ethernet interface
product: RTL8111/8168B PCI Express Gigabit Ethernet controller, vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: [EMAIL="pci@0000:01:00.0"]pci@0000:01:00.0[/EMAIL]
logical name: eth0
version: 03
serial: 20:cf:30:bf:23:b0
size: 100MB/s
capacity: 1GB/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.027.00-NAPI duplex=full ip=192.168.1.254 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
resources: irq:27 ioport:e800(size=256) memory:fdfff000-fdffffff(prefetchable) memory:fdff8000-fdffbfff(prefetchable) memory:febf0000-febfffff(prefetchable)
``````

eth0
Link encap:Ethernet  HWaddr 20:cf:30:bf:23:b0
inet addr:192.168.1.254
Bcast:192.168.1.255
Mask:255.255.255.0
inet6 addr: fe80::22cf:30ff:febf:23b0/64 Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
RX packets:301 errors:0 dropped:0 overruns:0 frame:0
TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:22095 (22.0 KB)  TX bytes:3167 (3.1 KB)
Interrupt:27 Base address:0x8000
lo
Link encap:Local Loopback
inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:64 errors:0 dropped:0 overruns:0 frame:0
TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:4740 (4.7 KB)  TX bytes:4740 (4.7 KB)
```

---

### Post by Iowan on 2012-02-19
Have you tried pinging from that machine? 
(gateway/router, internet via iP (8.8.8.8), etc.?)

---

### Post by praseodym on 2012-02-19
Hi,

change "false" to "true" in the file /etc/NetworkManager/NetworkManager.conf, otherwise the entries in the /etc/network/interfaces are ignored.

---

### Post by afanasiew on 2012-02-19
Excuse me, I'm pretty basic with this, how do I ping?

---

### Post by afanasiew on 2012-02-19
Changed 'false' to 'true' in *nm-system-settings.conf* and re-booted. Still to connection, but thanks for the suggestion.

---

### Post by Iowan on 2012-02-19
> **afanasiew said:**
> Excuse me, I'm pretty basic with this, how do I ping?
I prefer a terminal (Applications>Accessosries>terminal), but there's also a GUI version System>Administration>Network Tools>Ping

---

### Post by roelforg on 2012-02-20
> **afanasiew said:**
> Thanks for the response, Iowan.
 ```

eth0
Link encap:Ethernet  HWaddr 20:cf:30:bf:23:b0
inet addr:192.168.1.254
Bcast:192.168.1.255
Mask:255.255.255.0
inet6 addr: fe80::22cf:30ff:febf:23b0/64 Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
RX packets:301 errors:0 dropped:0 overruns:0 frame:0
TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:22095 (22.0 KB)  TX bytes:3167 (3.1 KB)
Interrupt:27 Base address:0x8000
lo
Link encap:Local Loopback
inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:64 errors:0 dropped:0 overruns:0 frame:0
TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:4740 (4.7 KB)  TX bytes:4740 (4.7 KB)
```

Post the content of /etc/network/interfaces,
try "sudo dhclient eth0" in a terminal, that ip looks like it's to high.
I've never seen any (sane configured, even with defaults) router/dhcp server dishing out ip's in such a high range. If the net won't work after the dhclient, try rebooting your router and flushing the dhcp-lease-table (or dhcp-leases ,,, check your manual for this).

---

### Post by afanasiew on 2012-02-20
Bizarre! Pinged 82.211.8.158 and got 0% successful packets after 5 requests. Pinged ubuntu.com and got 100%, during which my internet connection fixed itself after no further changes to settings! No comprende.
But thanks anyway, I guess.

---

### Post by afanasiew on 2012-02-20
> Post the content of /etc/network/interfaces,
try "sudo dhclient eth0" in a terminal, that ip looks like it's to high.
I've never seen any (sane configured, even with defaults) router/dhcp server dishing out ip's in such a high range. If the net won't work after the dhclient, try rebooting your router and flushing the dhcp-lease-table (or dhcp-leases ,,, check your manual for this).
 
tony@tony-desktop:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Listening on LPF/eth0/20:cf:30:bf:23:b0
Sending on LPF/eth0/20:cf:30:bf:23:b0
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.1.65 from 192.168.1.254
DHCPREQUEST of 192.168.1.65 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.65 from 192.168.1.254
bound to 192.168.1.65 -- renewal in 32769 seconds.
tony@tony-desktop:~$ ifconfig eth0
eth0
Link encap:Ethernet HWaddr 20:cf:30:bf:23:b0
inet addr:192.168.1.65
Bcast:192.168.1.255
Mask:255.255.255.0
inet6 addr: fe80::22cf:30ff:febf:23b0/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:1529 errors:0 dropped:0 overruns:0 frame:0
TX packets:909 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:2075880 (2.0 MB) TX bytes:76581 (76.5 KB)
Interrupt:27 Base address:0x8000
 
/etc/network/interfaces now reads:
 
auto eth0
iface eth0 inet static
address 192.168.1.254
netmask 255.255.255.0
network 192.168.1.255
broadcast 192.168.1.255
gateway 192.168.1.254
 
roelforg, thanks for your interest. I now have an internet connction, although I made no further changes to the settings you see above. I wait now to see if the connection remains stable.

---

### Post by afanasiew on 2012-02-20
> **praseodym said:**
> Hi,

change "false" to "true" in the file /etc/NetworkManager/NetworkManager.conf, otherwise the entries in the /etc/network/interfaces are ignored.
Apologies, praseodym, your fix may have worked after all. My internet connection mysteriously reappeared after a second reboot and after first being unavailable for 20 minutes. The network icon on the top bar has reappeared, displaying *ifupdown (eth0).*
If yours was the key fix, many thanks.

---

### Post by afanasiew on 2012-02-20
Oops, latest update in saga: connection lost again following reboot. :(

---

