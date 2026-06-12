---
title: "No LAN no WiFi networks"
date: 2012-08-07
forum: Networking &amp; Wireless
---

### Post by matthewh3 on 2012-08-07
Hi I'm trying to install Xubuntu on a new PC I got but I can get no LAN no WiFi networks but I can get my Android to tetyher to get online.

I've ran:    ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:02:44:5b:17:3f  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Base address:0xb800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:420 errors:0 dropped:0 overruns:0 frame:0
          TX packets:420 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:40026 (40.0 KB)  TX bytes:40026 (40.0 KB)

usb0      Link encap:Ethernet  HWaddr 8e:13:f4:3c:7d:4f  
          inet addr:192.168.100.100  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::8c13:f4ff:fe3c:7d4f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5226 errors:18 dropped:0 overruns:0 frame:18
          TX packets:4567 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5830600 (5.8 MB)  TX bytes:847874 (847.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:1f:14:35:7a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



and:   lspci -v | less

Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
        Subsystem: ASRock Incorporation Device 2570
        Flags: bus master, fast devsel, latency 0
        Memory at fe800000 (32-bit, prefetchable) [size=4M]
        Capabilities: <access denied>
        Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
        Subsystem: ASRock Incorporation Device 2572
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Memory at ff280000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at ec00 [size=8]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: <access denied>
        Kernel driver in use: i915
        Kernel modules: intelfb, i915

00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
        Flags: fast devsel
Memory at fecf0000 (32-bit, non-prefetchable) [size=4K]

00:1d.0 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ASRock Incorporation Device 24d0
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at dc00 [size=32]
        Kernel driver in use: uhci_hcd

00:1d.1 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ASRock Incorporation Device 24d0
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at e000 [size=32]
        Kernel driver in use: uhci_hcd

00:1d.2 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ASRock Incorporation Device 24d0
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at e400 [size=32]
        Kernel driver in use: uhci_hcd
00:1d.3 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ASRock Incorporation Device 24d0
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at e800 [size=32]
        Kernel driver in use: uhci_hcd

00:1d.7 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: ASRock Incorporation Device 24d0
        Flags: bus master, medium devsel, latency 0, IRQ 23
        Memory at ff27fc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
        Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: ff000000-ff0fffff
        Kernel modules: shpchp
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
        Flags: bus master, medium devsel, latency 0
        Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: ASRock Incorporation Device 24d0
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at fc00 [size=16]
        Memory at 20000000 (32-bit, non-prefetchable) [size=1K]
        Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: ASRock Incorporation Device 24d1
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
        I/O ports at d000 [size=8]
        I/O ports at cc00 [size=4]
I/O ports at c800 [size=8]
        I/O ports at c400 [size=4]
        I/O ports at c000 [size=16]
        Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
        Subsystem: ASRock Incorporation Device 24d0
        Flags: medium devsel, IRQ 5
        I/O ports at 0400 [size=32]
        Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
        Subsystem: ASRock Incorporation Device 9761
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at d800 [size=256]
        I/O ports at d400 [size=64]
        Memory at ff27f800 (32-bit, non-prefetchable) [size=512]
        Memory at ff27f400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
        Kernel driver in use: snd_intel8x0
        Kernel modules: snd-intel8x0
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+
        Flags: bus master, medium devsel, latency 32
        I/O ports at b800 [size=512]
        Memory at ff0ffc00 (32-bit, non-prefetchable) [size=512]
        Capabilities: <access denied>
        Kernel driver in use: 8139too
        Kernel modules: 8139too, 8139cp



Can anyone help?

---

### Post by praseodym on 2012-08-07
Please check

```
lsmod
lsusb
```

---

