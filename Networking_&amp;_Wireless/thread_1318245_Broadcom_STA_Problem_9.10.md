---
title: "Broadcom STA Problem 9.10"
date: 2009-11-07
forum: Networking &amp; Wireless
---

### Post by Eagl3 on 2009-11-07
Hello,

I seem to be having a problem with connecting to a wireless network. I just upgraded to Karmic and it is great. But there seems to be a problem with my proprietary drivers when it comes to the wireless. In the beginning no drivers would be detected at all for install. I did a manual update of everything for the system. Then the drivers showed up in the drivers manager window. I activated and rebooted. Now when i come back in ubuntu the switch of my wireless in the laptop actually controls when the wireless light on my computer turns on/off so thats a plus. However when I check on the wireless in ubuntu it says that the wireless network connection is disabled. I know the hardware works well because this is a dual-boot with windows xp and it works there. Also before 9.10 i had Jaunty running on this machine and the wireless worked perfectly. I am open to any suggestions about this problem. Thank you. Here are the info:

1) Machine Brand (Laptop)

```
Dell Vostro 1320
```

2)wireless brands/model
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
0e:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
1a:00.0 FireWire (IEEE 1394): O2 Micro, Inc. Device 10f7 (rev 01)
1a:00.1 SD Host controller: O2 Micro, Inc. Device 8120 (rev 01)
1a:00.2 Mass storage controller: O2 Micro, Inc. Device 8130 (rev 01)

```

3) interface
```
eagl3@eagl3-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:e8:c8:d2:d1  
          inet addr:192.168.1.68  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:e8ff:fec8:d2d1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1739 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1212 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1890386 (1.8 MB)  TX bytes:120522 (120.5 KB)
          Interrupt:31 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:25:56:3e:2e:4a  
          inet6 addr: fe80::225:56ff:fe3e:2e4a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

```

```
eagl3@eagl3-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated  
```

4) Modules
```
eagl3@eagl3-laptop:~$ lsmod | grep "wl"
wl                   1272936  0 
lib80211                6432  2 lib80211_crypt_tkip,wl

```

5) Kernel
```
eagl3@eagl3-laptop:~$ dmesg | grep "wl"
[   10.382586] wl: module license 'MIXED/Proprietary' taints kernel.
[   10.384523] wl 0000:0e:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   10.384533] wl 0000:0e:00.0: setting latency timer to 64

```

6)network config
```
sudo lshw -C network
[sudo] password for eagl3: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 03
       serial: 00:24:e8:c8:d2:d1
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.68 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:31 ioport:3000(size=256) memory:f6004000-f6004fff(prefetchable) memory:f6000000-f6003fff(prefetchable) memory:f6020000-f603ffff(prefetchable)
  *-network
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth1
       version: 01
       serial: 00:25:56:3e:2e:4a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:18 memory:fa000000-fa003fff

```


7)Scan for networks:
```
eagl3@eagl3-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

```

8)Version
```
Ubuntu 9.10
```

9)Kerrnel
```
2.6.31-14-generic i686

```

---

### Post by Eagl3 on 2009-11-08
bump, updated the output info, sorry about before.

---

