---
title: "how do i install drivers for atheros wierless lan in ubuntu 10.10"
date: 2011-01-03
forum: Networking &amp; Wireless
---

### Post by br9541 on 2011-01-03
Hi. Can anyone help me with installing drivers for an Atheros Wireless LAN.  I have searched online, and ether I can not find a solution to work or the instructions are to advanced for me to understand. thanks in advance.

---

### Post by PatchesTheCaveman on 2011-01-03
Hi br9541.  Happy New Year!

Most Atheros wireless cards work out of the box with Ubuntu.  To figure out why yours isn't working, we'll need to collect some diagnostic information.  To do that, go to Applications > Accessories > Terminal in your top panel.  Then type each of the following commands, pressing Enter after each one:
```
lspci -vnn
lshw -C network
ifconfig -a
uname -r
sudo iwconfig
```

After that last one, you'll need to type your password and press Enter.  It won't show up or show any stars or dots or anything, but it will work.

Once you're done with all that, copy everything and paste it into a reply to this thread.  All that info will help us figure out what's going on and tell you how to easily fix it.

---

### Post by Drone4four on 2011-06-29
I'm bumping this thread because I am experiencing a similar problem with my Atheros wireless card. It's particularly annoying because I have a deadline.  I want Ubuntu wireless working for tomorrow, the last day of PyCamp.  Up to this point I have been forced to learn python using Windows 7.  Ugh...

In my case, I am running both Windows 7 Starter 32bit and Ubuntu 11.04 natty 64bit. At home On Ubuntu I can connect to a local hotspot, but it disconnects sporadically in addition to being slow as molasses even while sitting right next to the wireless router. Even the sysadmin who deals with Linux on a daily basis couldn&#8217;t figure out how to connect my netbook to the in class wifi.  There is no router in the class room for me to plug my Ethernet wire into which is what I am using right now to make this forum post.

It's a brand new Acer Aspire One 533 series PAV01 with 2 GBs of ram. I followed Swarvey's instructions here:
[http://www.aspireoneuser.com/forum/viewtopic.php?f=6&t=24268&hilit=aao+drivers+look+here+first](http://www.aspireoneuser.com/forum/viewtopic.php?f=6&t=24268&hilit=aao+drivers+look+here+first)

I get stuck at step 6 because "Linux" isn't an option. The only download options on Acer's official drivers website are Windows 7 and Windows XP. I'm mighty pissed.

Here is the output of the commands PatchesTheCaveman suggests:

```

daniel@AO533:~$ lspci -vnn
00:00.0 Host bridge [0600]: Intel Corporation N10 Family DMI Bridge [8086:a010]
   Subsystem: Acer Incorporated [ALI] Device [1025:0349]
   Flags: bus master, fast devsel, latency 0
   Capabilities: <access denied>
   Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011] (prog-if 00 [VGA controller])
   Subsystem: Acer Incorporated [ALI] Device [1025:0349]
   Flags: bus master, fast devsel, latency 0, IRQ 44
   Memory at 98180000 (32-bit, non-prefetchable) [size=512K]
   I/O ports at 60c0 [size=8]
   Memory at 80000000 (32-bit, prefetchable) [size=256M]
   Memory at 98000000 (32-bit, non-prefetchable) [size=1M]
   Expansion ROM at <unassigned> [disabled]
   Capabilities: <access denied>
   Kernel driver in use: i915
   Kernel modules: i915

00:02.1 Display controller [0380]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a012]
   Subsystem: Acer Incorporated [ALI] Device [1025:0349]
   Flags: bus master, fast devsel, latency 0
   Memory at 98100000 (32-bit, non-prefetchable) [size=512K]
   Capabilities: <access denied>

00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
   Subsystem: Acer Incorporated [ALI] Device [1025:0349]
   Flags: bus master, fast devsel, latency 0, IRQ 45
   Memory at 98200000 (64-bit, non-prefetchable) [size=16K]
   Capabilities: <access denied>
   Kernel driver in use: HDA Intel
   Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02) (prog-if 00 [Normal decode])
   Flags: bus master, fast devsel, latency 0
   Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
   I/O behind bridge: 00005000-00005fff
   Memory behind bridge: 97000000-97ffffff
   Prefetchable memory behind bridge: 0000000090000000-0000000090ffffff
   Capabilities: <access denied>
   Kernel driver in use: pcieport
   Kernel modules: shpchp

00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02) (prog-if 00 [Normal decode])
   Flags: bus master, fast devsel, latency 0
   Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
   I/O behind bridge: 00004000-00004fff
   Memory behind bridge: 96000000-96ffffff
   Prefetchable memory behind bridge: 0000000091000000-0000000091ffffff
   Capabilities: <access denied>
   Kernel driver in use: pcieport
   Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02) (prog-if 00 [UHCI])
   Subsystem: Acer Incorporated [ALI] Device [1025:0349]
   Flags: bus master, medium devsel, latency 0, IRQ 16
   I/O ports at 6080 [size=32]
   Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02) (prog-if 00 [UHCI])
   Subsystem: Acer Incorporated [ALI] Device [1025:0349]
   Flags: bus master, medium devsel, latency 0, IRQ 17
   I/O ports at 6060 [size=32]
   Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02) (prog-if 00 [UHCI])
   Subsystem: Acer Incorporated [ALI] Device [1025:0349]
   Flags: bus master, medium devsel, latency 0, IRQ 18
   I/O ports at 6040 [size=32]
   Kernel driver in use: uhci_hcd

00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02) (prog-if 00 [UHCI])
   Subsystem: Acer Incorporated [ALI] Device [1025:0349]
   Flags: bus master, medium devsel, latency 0, IRQ 19
   I/O ports at 6020 [size=32]
   Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02) (prog-if 20 [EHCI])
   Subsystem: Acer Incorporated [ALI] Device [1025:0349]
   Flags: bus master, medium devsel, latency 0, IRQ 16
   Memory at 98204400 (32-bit, non-prefetchable) [size=1K]
   Capabilities: <access denied>
   Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2) (prog-if 01 [Subtractive decode])
   Flags: bus master, fast devsel, latency 0
   Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
   Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
   Subsystem: Acer Incorporated [ALI] Device [1025:0349]
   Flags: bus master, medium devsel, latency 0
   Capabilities: <access denied>
   Kernel modules: iTCO_wdt

00:1f.2 SATA controller [0106]: Intel Corporation N10/ICH7 Family SATA AHCI Controller [8086:27c1] (rev 02) (prog-if 01 [AHCI 1.0])
   Subsystem: Acer Incorporated [ALI] Device [1025:0349]
   Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 42
   I/O ports at 60b8 [size=8]
   I/O ports at 60cc [size=4]
   I/O ports at 60b0 [size=8]
   I/O ports at 60c8 [size=4]
   I/O ports at 60a0 [size=16]
   Memory at 98204000 (32-bit, non-prefetchable) [size=1K]
   Capabilities: <access denied>
   Kernel driver in use: ahci
   Kernel modules: ahci

00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
   Subsystem: Acer Incorporated [ALI] Device [1025:0349]
   Flags: medium devsel, IRQ 10
   I/O ports at 6000 [size=32]
   Kernel modules: i2c-i801

01:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
   Subsystem: Acer Incorporated [ALI] Device [1025:0349]
   Flags: bus master, fast devsel, latency 0, IRQ 43
   Memory at 97000000 (64-bit, non-prefetchable) [size=256K]
   I/O ports at 5000 [size=128]
   Capabilities: <access denied>
   Kernel driver in use: atl1c
   Kernel modules: atl1c

02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
   Subsystem: Foxconn International, Inc. Device [105b:e016]
   Flags: bus master, fast devsel, latency 0, IRQ 17
   Memory at 96000000 (64-bit, non-prefetchable) [size=64K]
   Capabilities: <access denied>
   Kernel driver in use: ath9k
   Kernel modules: ath9k

daniel@AO533:~$ sudo lshw -C network
[sudo] password for daniel:
 *-network               
      description: Ethernet interface
      product: AR8152 v1.1 Fast Ethernet
      vendor: Atheros Communications
      physical id: 0
      bus info: pci@0000:01:00.0
      logical name: eth0
      version: c1
      serial: 88:ae:1d:05:df:7b
      size: 100Mbit/s
      capacity: 100Mbit/s
      width: 64 bits
      clock: 33MHz
      capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
      configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.0.184 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
      resources: irq:43 memory:97000000-9703ffff ioport:5000(size=128)
 *-network
      description: Wireless interface
      product: AR9285 Wireless Network Adapter (PCI-Express)
      vendor: Atheros Communications Inc.
      physical id: 0
      bus info: pci@0000:02:00.0
      logical name: wlan0
      version: 01
      serial: 78:e4:00:30:c7:7c
      width: 64 bits
      clock: 33MHz
      capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
      configuration: broadcast=yes driver=ath9k driverversion=2.6.38-8-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
      resources: irq:17 memory:96000000-9600ffff
daniel@AO533:~$ lspci -vnn
00:00.0 Host bridge [0600]: Intel Corporation N10 Family DMI Bridge [8086:a010]
   Subsystem: Acer Incorporated [ALI] Device [1025:0349]
   Flags: bus master, fast devsel, latency 0
   Capabilities: <access denied>
   Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011] (prog-if 00 [VGA controller])
   Subsystem: Acer Incorporated [ALI] Device [1025:0349]
   Flags: bus master, fast devsel, latency 0, IRQ 44
   Memory at 98180000 (32-bit, non-prefetchable) [size=512K]
   I/O ports at 60c0 [size=8]
   Memory at 80000000 (32-bit, prefetchable) [size=256M]
   Memory at 98000000 (32-bit, non-prefetchable) [size=1M]
   Expansion ROM at <unassigned> [disabled]
   Capabilities: <access denied>
   Kernel driver in use: i915
   Kernel modules: i915

00:02.1 Display controller [0380]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a012]
   Subsystem: Acer Incorporated [ALI] Device [1025:0349]
   Flags: bus master, fast devsel, latency 0
   Memory at 98100000 (32-bit, non-prefetchable) [size=512K]
   Capabilities: <access denied>

00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
   Subsystem: Acer Incorporated [ALI] Device [1025:0349]
   Flags: bus master, fast devsel, latency 0, IRQ 45
   Memory at 98200000 (64-bit, non-prefetchable) [size=16K]
   Capabilities: <access denied>
   Kernel driver in use: HDA Intel
   Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02) (prog-if 00 [Normal decode])
   Flags: bus master, fast devsel, latency 0
   Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
   I/O behind bridge: 00005000-00005fff
   Memory behind bridge: 97000000-97ffffff
   Prefetchable memory behind bridge: 0000000090000000-0000000090ffffff
   Capabilities: <access denied>
   Kernel driver in use: pcieport
   Kernel modules: shpchp

00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02) (prog-if 00 [Normal decode])
   Flags: bus master, fast devsel, latency 0
   Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
   I/O behind bridge: 00004000-00004fff
   Memory behind bridge: 96000000-96ffffff
   Prefetchable memory behind bridge: 0000000091000000-0000000091ffffff
   Capabilities: <access denied>
   Kernel driver in use: pcieport
   Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02) (prog-if 00 [UHCI])
   Subsystem: Acer Incorporated [ALI] Device [1025:0349]
   Flags: bus master, medium devsel, latency 0, IRQ 16
   I/O ports at 6080 [size=32]
   Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02) (prog-if 00 [UHCI])
   Subsystem: Acer Incorporated [ALI] Device [1025:0349]
   Flags: bus master, medium devsel, latency 0, IRQ 17
   I/O ports at 6060 [size=32]
   Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02) (prog-if 00 [UHCI])
   Subsystem: Acer Incorporated [ALI] Device [1025:0349]
   Flags: bus master, medium devsel, latency 0, IRQ 18
   I/O ports at 6040 [size=32]
   Kernel driver in use: uhci_hcd

00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02) (prog-if 00 [UHCI])
   Subsystem: Acer Incorporated [ALI] Device [1025:0349]
   Flags: bus master, medium devsel, latency 0, IRQ 19
   I/O ports at 6020 [size=32]
   Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02) (prog-if 20 [EHCI])
   Subsystem: Acer Incorporated [ALI] Device [1025:0349]
   Flags: bus master, medium devsel, latency 0, IRQ 16
   Memory at 98204400 (32-bit, non-prefetchable) [size=1K]
   Capabilities: <access denied>
   Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2) (prog-if 01 [Subtractive decode])
   Flags: bus master, fast devsel, latency 0
   Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
   Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
   Subsystem: Acer Incorporated [ALI] Device [1025:0349]
   Flags: bus master, medium devsel, latency 0
   Capabilities: <access denied>
   Kernel modules: iTCO_wdt

00:1f.2 SATA controller [0106]: Intel Corporation N10/ICH7 Family SATA AHCI Controller [8086:27c1] (rev 02) (prog-if 01 [AHCI 1.0])
   Subsystem: Acer Incorporated [ALI] Device [1025:0349]
   Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 42
   I/O ports at 60b8 [size=8]
   I/O ports at 60cc [size=4]
   I/O ports at 60b0 [size=8]
   I/O ports at 60c8 [size=4]
   I/O ports at 60a0 [size=16]
   Memory at 98204000 (32-bit, non-prefetchable) [size=1K]
   Capabilities: <access denied>
   Kernel driver in use: ahci
   Kernel modules: ahci

00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
   Subsystem: Acer Incorporated [ALI] Device [1025:0349]
   Flags: medium devsel, IRQ 10
   I/O ports at 6000 [size=32]
   Kernel modules: i2c-i801

01:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
   Subsystem: Acer Incorporated [ALI] Device [1025:0349]
   Flags: bus master, fast devsel, latency 0, IRQ 43
   Memory at 97000000 (64-bit, non-prefetchable) [size=256K]
   I/O ports at 5000 [size=128]
   Capabilities: <access denied>
   Kernel driver in use: atl1c
   Kernel modules: atl1c

02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
   Subsystem: Foxconn International, Inc. Device [105b:e016]
   Flags: bus master, fast devsel, latency 0, IRQ 17
   Memory at 96000000 (64-bit, non-prefetchable) [size=64K]
   Capabilities: <access denied>
   Kernel driver in use: ath9k
   Kernel modules: ath9k

daniel@AO533:~$ sudo lshw -C network
 *-network               
      description: Ethernet interface
      product: AR8152 v1.1 Fast Ethernet
      vendor: Atheros Communications
      physical id: 0
      bus info: pci@0000:01:00.0
      logical name: eth0
      version: c1
      serial: 88:ae:1d:05:df:7b
      size: 100Mbit/s
      capacity: 100Mbit/s
      width: 64 bits
      clock: 33MHz
      capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
      configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.0.184 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
      resources: irq:43 memory:97000000-9703ffff ioport:5000(size=128)
 *-network
      description: Wireless interface
      product: AR9285 Wireless Network Adapter (PCI-Express)
      vendor: Atheros Communications Inc.
      physical id: 0
      bus info: pci@0000:02:00.0
      logical name: wlan0
      version: 01
      serial: 78:e4:00:30:c7:7c
      width: 64 bits
      clock: 33MHz
      capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
      configuration: broadcast=yes driver=ath9k driverversion=2.6.38-8-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
      resources: irq:17 memory:96000000-9600ffff
daniel@AO533:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 88:ae:1d:05:df:7b  
         inet addr:192.168.0.184  Bcast:192.168.0.255  Mask:255.255.255.0
         inet6 addr: fe80::8aae:1dff:fe05:df7b/64 Scope:Link
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
         RX packets:43992 errors:0 dropped:0 overruns:0 frame:0
         TX packets:20275 errors:0 dropped:0 overruns:0 carrier:1
         collisions:0 txqueuelen:1000
         RX bytes:57291146 (57.2 MB)  TX bytes:6840500 (6.8 MB)
         Interrupt:43

lo        Link encap:Local Loopback  
         inet addr:127.0.0.1  Mask:255.0.0.0
         inet6 addr: ::1/128 Scope:Host
         UP LOOPBACK RUNNING  MTU:16436  Metric:1
         RX packets:12 errors:0 dropped:0 overruns:0 frame:0
         TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0
         RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 78:e4:00:30:c7:7c  
         UP BROADCAST MULTICAST  MTU:1500  Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

daniel@AO533:~$ uname -r
2.6.38-8-generic
daniel@AO533:~$ uname -a
Linux AO533 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
daniel@AO533:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
         Mode:Managed  Access Point: Not-Associated   Tx-Power=17 dBm   
         Retry  long limit:7   RTS thr:off   Fragment thr:off
         Encryption key:off
         Power Management:off
         
daniel@AO533:~$

```

How do I get Ubuntu wireless working?

---

