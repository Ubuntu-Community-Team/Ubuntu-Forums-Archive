---
title: "Realtek 8111E driver r8168 issues"
date: 2013-03-04
forum: Networking &amp; Wireless
---

### Post by JimmyRcom on 2013-03-04
lubuntu 12.10 3.5.0-25-generic. The correct drivers seem to be loaded but it never gets an IP or successfully connects. I do get a green light when hooking in a cable, and it works fine on windows (separate drive).

Motherboard: GA-970A-D3 AM3+ 970 R
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813128521]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813128521&nm_mc=TEMC-RMA-Approvel&cm_mmc=TEMC-RMA-Approvel-_-Content-_-text-_-")

I followed the online [guides]("http://www.twm-kd.com/linux/realtek-rtl81688111e-and-ubuntu-linux/") and installed the drivers from realtek's website (r8168-8.028.00.tar.bz2). I also removed r8169 drivers. It seemed to install correctly but it still doesn't work.

_$ lspci -v_
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)    Subsystem: Giga-byte Technology GA-EP45-DS5/GA-EG45M-DS2H Motherboard
    Flags: bus master, fast devsel, latency 0, IRQ 73
    I/O ports at d000 [size=256]
    Memory at d0004000 (64-bit, prefetchable) [size=4K]
    Memory at d0000000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8168
    Kernel modules: r8168

_$ ifconfig_
eth1      Link encap:Ethernet  HWaddr 94:de:80:21:55:27  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:2 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:527 (527.0 B)  TX bytes:0 (0.0 B)
          Interrupt:73 Base address:0x6000 


_$ dmesg | grep 816_
[    0.471344] pci 0000:03:00.0: [10ec:8168] type 00 class 0x020000
[    1.523815] r8168 Gigabit Ethernet driver 8.035.00-NAPI loaded
[    1.523924] r8168 0000:03:00.0: irq 73 for MSI/MSI-X
[    1.524197] eth%d: RTL8168E-VL/8111E-VL at 0xffffc900125c6000, 94:de:80:21:55:27, IRQ 73
[    1.703344] r8168: This product is covered by one or more of the following patents: US5,307,459, US5,434,872, US5,732,094, US6,570,884, US6,115,776, and US6,327,625.
[    1.703347] eth0: Identified chip type is 'RTL8168E-VL/8111E-VL'.
[    1.703349] r8168  Copyright (C) 2012  Realtek NIC software team <nicfae@realtek.com> 
[    1.869816] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.608040] r8168: eth1: link down
[    4.169653] r8168: eth1: link up
[    4.604576] r8168: eth1: link up


r8168.ko is in
/lib/modules/3.5.0-25-generic/kernel/drivers/net/ethernet/realtek/
/lib/modules/3.5.0-25-generic/kernel/drivers/net/

It's added in text in /etc/modules
r8169 is blacklisted in  /etc/modprobe.d/blacklist.conf

_$ lsmod | grep 816_
[PHP]r8168                 248552  0[/PHP]

[B]I've tried:
[/B] restarting networking
shutting down, disconnecting power and ethernet, waiting forever, restarting
wake-on-lan enabled in windows on separate disk
there is no wake-on-lan option in motherboard, or least didn't see it
disabling ipv6
going to fry's electronic store for a different NIC. I searched on my phone and all 4 of their cards use a rebranded realtek which uses the r8169 driver I just purged.


leaning towards ordering an intel nic at this point online. Any help would be appreciated.

---

