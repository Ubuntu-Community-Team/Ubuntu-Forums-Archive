---
title: "AR9565 not working on 12.10.  LinuxWireless ath9k installed.  Network unclaimed."
date: 2012-12-24
forum: Networking &amp; Wireless
---

### Post by j814wong on 2012-12-24
I downloaded the drivers from linuxwireless and installed them using make make sudo install make unload And then I rebooted   Right clicking on the network button at the top right only has the &quot;Enable Networking&quot;, Edit, and a grayed out Information option.

_**lspci**_
```

00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM77 Express Chipset LPC Controller (rev 04)
00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5289 (rev 01)
01:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 0a)
02:00.0 Network controller: Atheros Communications Inc. AR9565 Wireless Network Adapter (rev 01)

```[U][B]

ifconfig
[/B][/U]```

eth0      Link encap:Ethernet  HWaddr 6c:3b:e5:7b:49:14  
          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::6e3b:e5ff:fe7b:4914/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2919 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2464 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2436959 (2.4 MB)  TX bytes:431481 (431.4 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:346 errors:0 dropped:0 overruns:0 frame:0
          TX packets:346 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:35885 (35.8 KB)  TX bytes:35885 (35.8 KB)

```[U][B]
sudo lshw -C network[/B][/U]
```

*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.2
       bus info: pci@0000:01:00.2
       logical name: eth0
       version: 0a
       serial: 6c:3b:e5:7b:49:14
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8411-1_0.0.3 06/18/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff
  *-network UNCLAIMED
       description: Network controller
       product: AR9565 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:c0500000-c057ffff memory:afb00000-afb0ffff

```The computer also seems to be picking up the drivers. 

_**modprobe -l**_ excerpt
```

updates/drivers/net/wireless/ath/ath.ko
updates/drivers/net/wireless/ath/ath9k/ath9k_common.ko
updates/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
updates/drivers/net/wireless/ath/ath9k/ath9k.ko
updates/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
updates/net/rfkill/rfkill-regulator.ko
updates/net/wireless/cfg80211.ko
updates/net/mac80211/mac80211.ko
updates/compat/compat.ko

```[U][B]

iwconfig
[/B][/U]```

eth0      no wireless extensions.

lo        no wireless extensions.

```

---

### Post by j814wong on 2012-12-25
Bump.

---

### Post by Pjotr123 on 2012-12-25
Try this roadmap:
[https://sites.google.com/site/easylinuxtipsproject/internet](https://sites.google.com/site/easylinuxtipsproject/internet)

---

