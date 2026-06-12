---
title: "No networking on a new motherboard"
date: 2013-08-15
forum: Networking &amp; Wireless
---

### Post by andyidol on 2013-08-15
Hello there!

I've replaced my old motherboard with the new one. Probably it's easier to say that i've connected HDD with installed **Ubuntu Server 13.04** to another computer. After that i can't get network to work.

I've tried this approach:
[http://www.serenux.com/2009/11/howto-fix-a-missing-eth0-adapter-after-moving-ubuntu-server-from-one-box-to-another/](http://www.serenux.com/2009/11/howto-fix-a-missing-eth0-adapter-after-moving-ubuntu-server-from-one-box-to-another/)
but it didn't really helped )

Here is the specs for my new motherboard (GIGABYTE GA-C847N, rev. 1.0):
[http://www.gigabyte.com/products/product-page.aspx?pid=4419#ov](http://www.gigabyte.com/products/product-page.aspx?pid=4419#ov)

It has two embedded Realtek Gigabit Ethernet adapters. My cable is connected to the first one and i have a good link indication, but networking is still not working.

Below is the list of some diagnostic commands.

**cat /etc/issue**
```

Ubuntu 13.04 \n \l

```

**uname -a**
```

Linux blackthorn 3.8.0-25-generic #37-Ubuntu SMP Thu Jun 6 20:47:07 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```

**sudo ifconfig -a**
```

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2340 (2.3 KB)  TX bytes:2340 (2.3 KB)


p1p1      Link encap:Ethernet  HWaddr 90:2b:34:d9:18:ec  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


p1p2      Link encap:Ethernet  HWaddr 90:2b:34:d9:18:ee  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

**sudo lshw -C network**
```

  *-network DISABLED
       description: Ethernet interface
       product: RTL8111/8168 PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: p1p1
       version: 06
       serial: 90:2b:34:d9:18:ec
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:40 ioport:e000(size=256) memory:f7d00000-f7d00fff memory:f0100000-f0103fff
  *-network DISABLED
       description: Ethernet interface
       product: RTL8111/8168 PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: p1p2
       version: 06
       serial: 90:2b:34:d9:18:ee
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=no multicast=yes port=MII speed=100Mbit/s
       resources: irq:41 ioport:d000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff

```

**lspci -nn**
```

00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0106] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 [8086:1e3a] (rev 04)
00:1a.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 [8086:1e10] (rev c4)
00:1c.1 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 [8086:1e12] (rev c4)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev c4)
00:1c.3 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 [8086:1e16] (rev c4)
00:1d.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation 7 Series Chipset Family LPC Controller [8086:1e5f] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] [8086:1e03] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller [8086:1e22] (rev 04)
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
03:00.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 41)
05:00.0 IDE interface [0101]: JMicron Technology Corp. JMB368 IDE controller [197b:2368]

```

**dmesg | grep -i net**
```

[    0.115134] NET: Registered protocol family 16
[    0.197472] NetLabel: Initializing
[    0.197478] NetLabel:  domain hash size = 128
[    0.197482] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.197501] NetLabel:  unlabeled traffic allowed by default
[    0.220338] NET: Registered protocol family 2
[    0.221625] NET: Registered protocol family 1
[    0.791640] audit: initializing netlink socket (disabled)
[    0.942152] NET: Registered protocol family 10
[    0.942413] NET: Registered protocol family 17
[    1.070359] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.093678] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    6.150629] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    6.150642] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[    6.660343] type=1400 audit(1376620012.200:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=474 comm="apparmor_parser"
[    6.667021] type=1400 audit(1376620012.204:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=473 comm="apparmor_parser"
[    6.927386] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    8.879376] FS-Cache: Netfs 'nfs' registered for caching
[  129.035698] type=1400 audit(1376620134.576:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=908 comm="apparmor_parser"
[  129.241946] NFSD: starting 90-second grace period (net ffffffff81cbafc0)
[  129.498863] ip_tables: (C) 2000-2006 Netfilter Core Team

```

Looks like adapters are "disabled" for some reason. How do i "enable" them?

Please advise! Thanks = )

---

### Post by andyidol on 2013-08-15
Oh, i've just figured this out by myself = )

I've added following lines to my /etc/network/interfaces:

# Interface 1
auto p1p1
iface p1p1 inet dhcp

# Interface 2
auto p1p2
iface p1p2 inet dhcp

And then removed an old configuration from this file for an "eth0" interface.

After that i've just hit: **sudo ifup p1p1** to bring this interface up.

P/S: and if you are going to use only one interface, just remove or comment-out configuration for the second one (otherwise you will get lengthy "waiting for network configuration" process during boot).

Sorry for the trouble )

Maybe my post will help someone though = )

---

