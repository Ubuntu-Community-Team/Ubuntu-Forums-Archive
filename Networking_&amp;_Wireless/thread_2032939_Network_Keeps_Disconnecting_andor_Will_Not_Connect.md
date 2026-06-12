---
title: "Network Keeps Disconnecting and/or Will Not Connect"
date: 2012-07-25
forum: Networking &amp; Wireless
---

### Post by Chilli Bob on 2012-07-25
Hi all, I would appreciate any help I can get with this problem.  I have been using Xubuntu 12.04 for some weeks with no problems at all.  Then yesterday I booted up and the WIFI did not connect and I got the notification "NETWORK   Disconnected - you are now offline".  When I right-click on the network icon and sellect "enable networking", it doesn't connect and I immediatly get the "NETWORK   Disconnected - you are now offline" notification again.  Unfortunately I don't have a windows partition or a live CD handy to test if this is a hardware issue.

I have looked online for an answer, but most of the information relates to laptops and issues with rfkill, which does not apply to me.

 I have a home-built desktop ( i3 with Intel Mobo).  I have a PCI wireless card (not sure what brand, netgear I think).  I have put he output of what appear to be the mopst usefull commands below.

if config
```

XXXX:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr e0:69:95:57:ff:9d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:fe600000-fe620000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:188 errors:0 dropped:0 overruns:0 frame:0
          TX packets:188 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14064 (14.0 KB)  TX bytes:14064 (14.0 KB)
```
sudo lshw -C network

```
XXXX:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82579V Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 05
       serial: e0:69:95:57:ff:9d
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k firmware=0.13-4 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:48 memory:fe600000-fe61ffff memory:fe628000-fe628fff ioport:f080(size=32)
  *-network UNCLAIMED
       description: Network controller
       product: RT2561/RT61 rev B 802.11g
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64
       resources: memory:fe500000-fe507fff
```
lspci -nn
```

XXXX:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0100] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0102] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
00:19.0 Ethernet controller [0200]: Intel Corporation 82579V Gigabit Network Connection [8086:1503] (rev 05)
00:1a.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b5)
00:1c.3 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 [8086:1c16] (rev b5)
00:1d.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 05)
00:1f.0 ISA bridge [0601]: Intel Corporation H67 Express Chipset Family LPC Controller [8086:1c4a] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 6 Series/C200 Series Chipset Family SATA AHCI Controller [8086:1c02] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller [8086:1c22] (rev 05)
01:00.0 PCI bridge [0604]: Integrated Technology Express, Inc. Device [1283:8892] (rev 10)
02:00.0 Network controller [0280]: Ralink corp. RT2561/RT61 rev B 802.11g [1814:0302]
03:00.0 USB controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 03)

```
sudo iwlist scan

```
XXXX:~$ sudo iwlist scan
[sudo] password for rob: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```

lsusb

```
XXXX:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 045e:0750 Microsoft Corp. Wired Keyboard 600
Bus 001 Device 004: ID 045e:0083 Microsoft Corp. Basic Optical Mouse
```Thanks again for any help,

Rob

---

### Post by Chilli Bob on 2012-07-26
BUMP!

Anyone able to help?

---

