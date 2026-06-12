---
title: "Drivers loaded, hoe to bind to eth1?"
date: 2006-06-23
forum: Networking &amp; Wireless
---

### Post by Syzzer on 2006-06-23
This morning, I installed an Intel Gbit Ethernetcard into my system. At he moment I managed to understand why I is is no problem the Intel driver won't install.
> syzzer@syzzer-server:~/e1000-7.1.9/src$ make install
Makefile:66: *** Linux kernel source not found.  Stop.

The module is already available and loaded in Ubuntu:
> syzzer@syzzer-server:~/e1000-7.1.9/src$ lsmod | grep e1000
e1000                 127288  0
and
> syzzer@syzzer-server:~/e1000-7.1.9/src$ sudo lshw -C network
Password:
  *-network UNCLAIMED
       description: Ethernet controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@02:00.0
       version: 06
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       resources: iomemory:feae0000-feafffff iomemory:feac0000-feadffff ioport:d800-d81f irq:217
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@03:03.0
       logical name: eth0
       version: 10
       serial: 00:13:d3:f1:ab:0d
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=172.20.26.40 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:e800-e8ff iomemory:febffc00-febffcff irq:233

But my ifconfig amkes no notice of this card:
> syzzer@syzzer-server:~/e1000-7.1.9/src$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:13:D3:F1:AB:0D
          inet addr:172.20.26.40  Bcast:172.20.27.255  Mask:255.255.252.0
          inet6 addr: fe80::213:d3ff:fef1:ab0d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13198 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2873 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1510193 (1.4 MiB)  TX bytes:309687 (302.4 KiB)
          Interrupt:233 Base address:0xcc00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

So, I think the only thing left to do is to bind the hardware to eth1. The problem here: I've been searching the internet and these forums to find out how to do this, but wasn't able to find a way.

Who can push me into the right direction to make the next step?

---

### Post by Syzzer on 2006-06-23
I've been searching an bit further and found these lines in dmesg:
> [   28.272857] 8139too Fast Ethernet driver 0.9.27
[   28.272909] GSI 20 sharing vector 0xE9 and IRQ 20
[   28.272912] ACPI: PCI Interrupt 0000:03:03.0[A] -> GSI 20 (level, low) -> IRQ 233
[   28.273681] eth0: RealTek RTL8139 at 0xffffc2001009cc00, 00:13:d3:f1:ab:0d, IRQ 233
[   28.273685] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   28.285814] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[   28.324815] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   28.382088] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   28.609919] Intel(R) PRO/1000 Network Driver - version 7.0.33-k2
[   28.609923] Copyright (c) 1999-2005 Intel Corporation.
[   28.609976] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 217
[   28.609990] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   28.610006] e1000: 0000:02:00.0: e1000_sw_init: Unknown MAC Type
[   28.610172] e1000: probe of 0000:02:00.0 failed with error -5
[   28.837518] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 217
[   28.943276] eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
It seems this is why eth1 is not created. I've been searching on the e1000 errors, but all I find is the sourcecode for the driver.

Who does know what this means and how to fix it?

---

### Post by digitalpardoe on 2006-06-23
I was having problems with my set up. Basically the same thing as you I think. This post really helped me: [http://ubuntuforums.org/showthread.php?t=87643]("http://ubuntuforums.org/showthread.php?t=87643").

Basically I had to:

```

sudo ifconfig eth1 up
sudo dhclient eth1

```

But I had Webmin installed with Network Configuration to set everything in stone, or at least in boot.

---

