---
title: "new nic, strange problems"
date: 2010-02-13
forum: Networking &amp; Wireless
---

### Post by bender1234 on 2010-02-13
Hi.

I just installed a new NIC on my server, and the plan was to run the box as a router.
An odd thing happens, when I boot the system it may take a long time for it to start.
when running ifconfig neither eth0 nor eth1 appears.

uname -a
```
Linux server910 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 i686 GNU/Linux
```


If I wipe /etc/udev/rules.d/70-persistent-net.rules and boot it brings up one of the cards.

lshw -C network
```
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:01:06.0
       logical name: eth0
       version: 10
       serial: 90:e6:ba:24:ca:90
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.0.196 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:16 ioport:d800(size=256) memory:f7fffc00-f7fffcff memory:80000000-8001ffff(prefetchable)
  *-network DISABLED
       description: Ethernet interface
       product: MCP77 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth1
       version: a2
       serial: 90:e6:ba:24:ca:90
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.64 latency=0 maxlatency=20 mingnt=1 multicast=yes
       resources: irq:22 memory:f7e7c000-f7e7cfff ioport:b880(size=8) memory:f7e7f400-f7e7f4ff memory:f7e7f000-f7e7f00f

```I've removed dhcp3-server and reverted to:

auto lo
iface lo inet loopback

and
auto ethx
iface ethx inet dhcp

on both devices in /etc/network/interfaces

ifconfig -a 
```
eth0      Link encap:Ethernet  HWaddr 90:e6:ba:24:ca:90  
          inet addr:192.168.0.196  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::92e6:baff:fe24:ca90/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1073 errors:0 dropped:0 overruns:0 frame:0
          TX packets:995 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1127177 (1.1 MB)  TX bytes:188676 (188.6 KB)
          Interrupt:16 Base address:0x8c00 

eth1      Link encap:Ethernet  HWaddr 90:e6:ba:24:ca:90  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:996 (996.0 B)  TX bytes:996 (996.0 B)

```Any ideas how to solve the issue? the RTL card is the new NIC. As stated earlier if I don't wipe
/etc/udev/rules.d/70-persistent-net.rules either no card gets "started", or just one. The odd thing
is at on a couple of boots it swaps which gets started. And the interface may get odd names such as
eth1_renamed and a<something>_eth1/0.


dmesg | grep eth
```
[    1.684242] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.684607] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 22 (level, low) -> IRQ 22
[    1.684611] forcedeth 0000:00:0a.0: setting latency timer to 64
[    1.707518] eth0: RTL8169sb/8110sb at 0xf8118c00, 90:e6:ba:24:ca:90, XID 10000000 IRQ 16
[    1.746253] forcedeth 0000:00:0a.0: ifname eth1, PHY OUI 0x732 @ 3, addr 90:e6:ba:24:ca:90
[    1.746257] forcedeth 0000:00:0a.0: highdma csum pwrctl mgmt gbit lnktim msi desc-v3
[   10.125587] r8169: eth0: link up
[   20.292008] eth0: no IPv6 routers present

```I can try getting the info for when all is wacked, compared to now when one card is up.
Any pointers would be greatly appreciated.

regard,
bender

---

### Post by bender1234 on 2010-02-13
Ok when starting without the wipe ifconfig just shows the lo interface.
One thing that's really strange here is that the two cards are given
the same MAC address in both cases(!!!).

ifconfig -a shows

```
eth1      Link encap:Ethernet  HWaddr 90:e6:ba:24:ca:90  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Base address:0x8000 

eth0_rename Link encap:Ethernet  HWaddr 90:e6:ba:24:ca:90  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0x2c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

```lshw -C network
```
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:01:06.0
       logical name: eth0_rename
       version: 10
       serial: 90:e6:ba:24:ca:90
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:16 ioport:d800(size=256) memory:f7fffc00-f7fffcff memory:80000000-8001ffff(prefetchable)
  *-network DISABLED
       description: Ethernet interface
       product: MCP77 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth1
       version: a2
       serial: 90:e6:ba:24:ca:90
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.64 latency=0 maxlatency=20 mingnt=1 multicast=yes
       resources: irq:22 memory:f7e7c000-f7e7cfff ioport:b880(size=8) memory:f7e7f400-f7e7f4ff memory:f7e7f000-f7e7f00f
```cat /etc/udev/rules.d/70-persistent-net.rules
```
# PCI device 0x10ec:0x8169 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="90:e6:ba:24:ca:90", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10de:0x0760 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="90:e6:ba:24:ca:90", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

```dmesg | grep eth
```
[    1.704627] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.704974] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 22 (level, low) -> IRQ 22
[    1.704977] forcedeth 0000:00:0a.0: setting latency timer to 64
[    1.714050] eth0: RTL8169sb/8110sb at 0xf8132c00, 90:e6:ba:24:ca:90, XID 10000000 IRQ 16
[    1.770920] forcedeth 0000:00:0a.0: ifname eth1, PHY OUI 0x732 @ 3, addr 90:e6:ba:24:ca:90
[    1.770925] forcedeth 0000:00:0a.0: highdma csum pwrctl mgmt gbit lnktim msi desc-v3

```Any bright ideas? I'm kind of blank myself here, haven't even heard of /etc/udev/rules.d/70-persistent-net.rules until googling for a solution. How does this thing work? Thought it would be obvious to bind interfacenames to MAC addresses, and that this file would do just that. 

And I might add that the old nvidia NIC is on an asus M4N78-SE board, and the new nic is a cnet ProG-2000S.

---

