---
title: "Intel 82567LM e1000e network driver failed in Ubuntu"
date: 2010-05-31
forum: Networking &amp; Wireless
---

### Post by treefly on 2010-05-31
When I install Ubuntu 10.0.4 in Dell E6500, ubuntu cannot regonize the network driver.
Here are some command and its result in my environment, does anyone have idea about it? Thanks very much.

sudo cat /var/log/messages | grep -i e1000e
-----------------------------------------------------------------------------------------------------------------
May 31 14:59:42 echo-laptop kernel: [    0.940441] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
May 31 14:59:42 echo-laptop kernel: [    0.940444] e1000e: Copyright (c) 1999-2008 Intel Corporation.
May 31 14:59:42 echo-laptop kernel: [    0.940486] e1000e 0000:00:19.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
May 31 14:59:42 echo-laptop kernel: [    1.070827] e1000e 0000:00:19.0: PCI INT A disabled
May 31 14:59:42 echo-laptop kernel: [    1.070833] e1000e: probe of 0000:00:19.0 failed with error -5

sudo lshw -C network
-----------------------------------------------------------------------------------------------------------------
  *-network UNCLAIMED     
       description: Ethernet controller
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi cap_list
       configuration: latency=0
       resources: memory:f6fe0000-f6ffffff memory:f6fdb000-f6fdbfff ioport:efe0(size=32)
  *-network
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:25:56:1f:fc:d1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.0.36 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:f1ffc000-f1ffffff

lspci -v | grep Eth
-----------------------------------------------------------------------------------------------------------------
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)

ifconfig
-----------------------------------------------------------------------------------------------------------------
eth1      Link encap:Ethernet  HWaddr 00:25:56:1f:fc:d1  
          inet addr:192.168.0.36  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::225:56ff:fe1f:fcd1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2367 errors:0 dropped:0 overruns:0 frame:13786
          TX packets:1676 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2242099 (2.2 MB)  TX bytes:281398 (281.3 KB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

uname -a
-----------------------------------------------------------------------------------------------------------------
Linux echo-laptop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux

---

### Post by treefly on 2010-06-21
Does anyone help me for this?

---

### Post by ryanfmac on 2011-12-16
same problem here on the same system.  any solution?

---

