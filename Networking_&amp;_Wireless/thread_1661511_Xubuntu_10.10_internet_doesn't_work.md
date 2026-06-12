---
title: "Xubuntu 10.10 internet doesn't work"
date: 2011-01-06
forum: Networking &amp; Wireless
---

### Post by phoenixrising186 on 2011-01-06
I've recently installed Xubuntu 10.10 onto my Dell Inspiron Mini (I think 1011), and found that my internet flat out doesn't work, wired or wireless. When I connect the netbook to an ethernet wire, it says I am connected, but fails to load any pages or connect to the internet for any purpose (updater, drivers, etc.). Additionally, my wireless does not work, and in the panel under wireless networks it says "device not ready (firmware missing)".

I am sure this post is missing vital information that would help fix my problem, so if anyone would be so kind as to tell me what I need to post so that people can help me find a solution, I'd be very grateful. I am not a computer-oriented person, and this is my first time using Linux. Any help would be greatly appreciated!

---

### Post by PatchesTheCaveman on 2011-01-07
To get your wireless working, you likely need to install the Broadcom drivers.  You can do that in System > Administration > Addtional Drivers (or Hardware Drivers in 10.04 LTS).

Most people don't have trouble with their wired connection though, to troubleshoot that, plug in to your wired Ethernet connection and go to Applications > Accessories > Terminal and type each of the following commands, pressing Enter after each one:
```
lspci -vnn
lshw -C network
ifconfig -a
```

Copy and paste the output to a reply to this post.

---

### Post by phoenixrising186 on 2011-01-07
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)
    Subsystem: Dell Device [1028:02f4]
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03) (prog-if 00 [VGA controller])
    Subsystem: Dell Device [1028:02f4]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f0000000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at 1800 [size=8]
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    Memory at f0200000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
    Subsystem: Dell Device [1028:02f4]
    Flags: bus master, fast devsel, latency 0
    Memory at f0080000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
    Subsystem: Dell Device [1028:02f4]
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at f0440000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: 40000000-401fffff
    Prefetchable memory behind bridge: 0000000040200000-00000000403fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: f0100000-f01fffff
    Prefetchable memory behind bridge: 0000000040400000-00000000405fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: 40600000-409fffff
    Prefetchable memory behind bridge: 00000000f0500000-00000000f05fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Device [1028:02f4]
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at 1820 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Device [1028:02f4]
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 1840 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Device [1028:02f4]
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 1860 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Device [1028:02f4]
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 1880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02) (prog-if 20 [EHCI])
    Subsystem: Dell Device [1028:02f4]
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f0444000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
    Subsystem: Dell Device [1028:02f4]
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: leds-ss4200, iTCO_wdt, intel-rng

00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02) (prog-if 8a [Master SecP PriP])
    Subsystem: Dell Device [1028:02f4]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 1810 [size=16]
    Memory at 40a00000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
    Subsystem: Dell Device [1028:02f4]
    Flags: medium devsel, IRQ 10
    I/O ports at 18c0 [size=32]
    Kernel modules: i2c-i801

03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f0100000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb

04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Dell Device [1028:02f4]
    Flags: bus master, fast devsel, latency 0, IRQ 43
    I/O ports at 2000 [size=256]
    Memory at f0510000 (64-bit, prefetchable) [size=4K]
    Memory at f0500000 (64-bit, prefetchable) [size=64K]
    [virtual] Expansion ROM at f0520000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

----

  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f0100000-f0103fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:24:e8:ed:2b:d0
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=10.21.149.68 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:43 ioport:2000(size=256) memory:f0510000-f0510fff memory:f0500000-f050ffff memory:f0520000-f053ffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 90:4c:e5:21:a7:a0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-22-generic firmware=N/A link=yes multicast=yes wireless=IEEE 802.11bg

----

eth0      Link encap:Ethernet  HWaddr 00:24:e8:ed:2b:d0  
          inet addr:10.21.149.68  Bcast:10.21.149.127  Mask:255.255.255.128
          inet6 addr: fe80::224:e8ff:feed:2bd0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1555 errors:0 dropped:0 overruns:0 frame:0
          TX packets:272 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:169469 (169.4 KB)  TX bytes:17176 (17.1 KB)
          Interrupt:43 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19290 (19.2 KB)  TX bytes:19290 (19.2 KB)

wlan0     Link encap:Ethernet  HWaddr 90:4c:e5:21:a7:a0  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



That's what I get when I paste those commands into the terminal, hope it helps!

---

### Post by PatchesTheCaveman on 2011-01-07
Okay, it looks like your computer is getting an IP address from your router, which is good.  Have you tried resetting the router?  Unplug it, wait 30 seconds, and plug it back in.  That fixes a lot of peoples' problems.

If it doesn't, I have a few more commands for you.  First:
```
ping google.com
```
Let that run for about 30 seconds and then press CTRL+C to stop it.

Then run this one:
```
ping 8.8.8.8
```
Let that one run for about 30 seconds to and then CTRL+C again.

One more:
```
ip route show
```

Copy and paste the results of all that in another post and hopefully we can sort this out.

---

### Post by phoenixrising186 on 2011-01-14
Sorry for responding so late, my regular computer got lost and I had no way of communicating with this thread, but fortunately I managed to get the Ethernet working!

To do so, I took my netbook to class with me and plugged it in via the wall jack and updated the OS and installed the b43 drivers for my broadcom wireless card. When I attempted to connect to the wireless, it worked, and let me go on the internet and everything. However, after about 5 minutes the connection just went down, and won't let me back on.

Everytime I restart it does this, works for about 1-5 minutes, then breaks. I took the netbook to the helpdesk here on my campus (I go to RIT in upstate new york), and the local linux user couldn't figure it out. 

Any ideas?

---

### Post by PatchesTheCaveman on 2011-01-14
Try using the official STA driver from Broadcom instead.  To install it, run this command on a terminal:
```
sudo apt-get install bcmwl-kernel-source
```

Then, disable the b43 driver and activate the STA driver:
```
sudo modprobe -r b43
sudo modprobe wl
```

Now, see if it works better.  If it does, permanently disable the b43 driver:
```
sudo bash -c "echo blacklist b43 >> /etc/modprobe.d/blacklist.conf"
```

If it doesn't, switch back and permanently disable the STA driver:
```
sudo modprobe -r wl
sudo modprobe b43
sudo bash -c "echo blacklist wl >> /etc/modprobe.d/blacklist.conf"
```

---

### Post by phoenixrising186 on 2011-01-20
I think that did the trick. After disabling the b43 driver and enabling the STA one, the internet now works, although it takes some time to connect on startup (~30 seconds).

Thank you so much for your help, I really appreciate it!

---

### Post by phoenixrising186 on 2011-01-20
I think that did the trick. After disabling the b43 driver and enabling the STA one, the internet now works, although it takes some time to connect on startup (~30 seconds).

Thank you so much for your help, I really appreciate it!

---

