---
title: "Gigabit network is not working (r8169 driver problem)"
date: 2011-01-14
forum: Networking &amp; Wireless
---

### Post by Gasoile on 2011-01-14
Hi everybody!

I have a pc that used to run IPCop in a VM under Windows and now I changed the main system to Ubuntu 10.10 x64 (2.6.35-24-generic), But the gigabit network adapters (eth0 - Realtek RTL8111/8168B, eth1,2 - D-Link DGE-528T) only works at 100Mbps.
I did search for this problem and find out that at least the Realtek adapter should work with the r8168 driver, but couldn't find a solution to put all the 3 adapters working correctly! Someone knows how to solve this problem?

Here it is some information about my system:

dmesg:
```
[    1.958343] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.958365] r8169 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.958404] r8169 0000:02:00.0: setting latency timer to 64
[    1.958468] r8169 0000:02:00.0: irq 42 for MSI/MSI-X
[    1.959153] r8169 0000:02:00.0: eth0: RTL8168b/8111b at 0xffffc90000352000, 00:1d:7d:d7:dd:07, XID 18000000 IRQ 42
[    1.964803] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.964841] r8169 0000:03:06.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.964875] r8169 0000:03:06.0: (unregistered net_device): no PCI Express capability
[    1.965497] r8169 0000:03:06.0: eth1: RTL8169sb/8110sb at 0xffffc9000035a000, f0:7d:68:d0:b7:64, XID 10000000 IRQ 20
[    1.970991] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.971030] r8169 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.971066] r8169 0000:03:07.0: (unregistered net_device): no PCI Express capability
[    1.971715] r8169 0000:03:07.0: eth2: RTL8169sb/8110sb at 0xffffc90000376000, 00:1c:f0:bb:08:4b, XID 10000000 IRQ 21
[   12.970548] r8169 0000:02:00.0: eth0: link down
[   12.993618] r8169 0000:03:06.0: eth1: link up
[   12.995666] r8169 0000:03:07.0: eth2: link down
[ 2170.812312] r8169 0000:03:06.0: eth1: link down
[ 2185.304817] r8169 0000:03:06.0: eth1: link up
[ 3125.650894] r8169 0000:03:06.0: eth1: link down
[ 3140.287398] r8169 0000:03:06.0: eth1: link up
[ 5210.923479] r8169 0000:03:06.0: eth1: link down
[ 5225.406766] r8169 0000:03:06.0: eth1: link up
```

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:1d:7d:d7:dd:07  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr f0:7d:68:d0:b7:64  
          inet addr:192.168.1.110  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::f27d:68ff:fed0:b764/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:269630 errors:0 dropped:0 overruns:0 frame:0
          TX packets:267357 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:224019180 (224.0 MB)  TX bytes:178728294 (178.7 MB)
          Interrupt:20 Base address:0xa000 

eth2      Link encap:Ethernet  HWaddr 00:1c:f0:bb:08:4b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0x6000 
```

lspci:
```
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:06.0 Ethernet controller: D-Link System Inc DGE-528T Gigabit Ethernet Adapter (rev 10)
03:07.0 Ethernet controller: D-Link System Inc DGE-528T Gigabit Ethernet Adapter (rev 10)
```

Thanks

---

### Post by mesfet on 2011-01-25
Hello.
I have the same problem with two DIGITUS gigabit ethernet pci express network card (DN-1013-2).
Regards. Paolo

---

### Post by uaebuntu on 2011-05-10
I'm running 10.10 32 bit

jim@venus:~$ uname -r
2.6.35-28-generic

I've just added a D-Link DGE-528T Gigabit Ethernet adapter for access to my NAS, still have the old NIC installed. Bought it as D-Link is a reputable brand and it said Linux compatible on the box! Wish I'd read all the posts first!

I added the card and booted up.Card does not work.

jim@venus:~$ dmesg | grep Ethernet
[    1.230744] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded

and lspci shows both NICs

02:02.0 Ethernet controller: D-Link System Inc DGE-528T Gigabit Ethernet Adapter (rev 10)
02:04.0 Ethernet controller: VIA Technologies, Inc. VT6105/VT6106S [Rhine-III] (rev 86

So I guess that tells me the card and the driver are there, but everything else I've tried shows the card as inoperative. There are tons of posts of similar problems but no simple solution to get the card up and running.

Any Ideas

---

