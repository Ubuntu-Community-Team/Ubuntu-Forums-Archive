---
title: "no internet with static ip address"
date: 2013-08-18
forum: Networking &amp; Wireless
---

### Post by dionysius65 on 2013-08-18
I do apologize for failing to find the answer on my own. I've been looking for 10+ hours on how to get a static address.

Here is the output of all the command requests I could find for similar issues. I've also attempted to llok at any log files I'm aware of and still no go.

*****uname -r
3.8.0-29-generic

*****root@zd8000-EC303UA-ABA:/home/frank3# cat /etc/network/interfaces
auto lo
iface lo inet loopback

root@zd8000-EC303UA-ABA:/home/frank3# 

*****root@zd8000-EC303UA-ABA:/home/frank3# cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=true
root@zd8000-EC303UA-ABA:/home/frank3# 

*****root@zd8000-EC303UA-ABA:/home/frank3# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:ca:56:5d  
          inet addr:192.168.1.254  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:feca:565d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:562 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1258 (1.2 KB)  TX bytes:48687 (48.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:539 errors:0 dropped:0 overruns:0 frame:0
          TX packets:539 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:46025 (46.0 KB)  TX bytes:46025 (46.0 KB)


*****root@zd8000-EC303UA-ABA:/home/frank3# netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG        0 0          0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
root@zd8000-EC303UA-ABA:/home/frank3# 

*****root@zd8000-EC303UA-ABA:/home/frank3# dmesg | grep eth
[    0.165176] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7022d38), AE_ALREADY_EXISTS (20121018/psparse-537)
[    0.165186] ACPI: Marking method _OSC as Serialized because of AE_ALREADY_EXISTS error
[    0.170059] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7022d38), AE_ALREADY_EXISTS (20121018/psparse-537)
[    1.846503] 8139too 0000:0b:02.0 eth0: RealTek RTL8139 at 0x00015000, 00:c0:9f:ca:56:5d, IRQ 20
[    6.754459] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.344605] 8139too 0000:0b:02.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
root@zd8000-EC303UA-ABA:/home/frank3# 

*****root@zd8000-EC303UA-ABA:/home/frank3# lspci -vnn | grep -A2 -e "\[0200\]" -e "\[0280\]"
0b:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:3082]
    Flags: bus master, medium devsel, latency 64, IRQ 20
--
0b:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
    Subsystem: Hewlett-Packard Company Broadcom 802.11b/g WLAN [103c:12f8]
    Flags: fast devsel, IRQ 5
root@zd8000-EC303UA-ABA:/home/frank3# 

*****root@zd8000-EC303UA-ABA:/home/frank3# ping 192.168.1.254
PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data.
From 192.168.1.125 icmp_seq=1 Destination Host Unreachable
^C
--- 192.168.1.254 ping statistics ---
4 packets transmitted, 0 received, +1 errors, 100% packet loss, time 2999ms

  *-network:0
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:0b:02.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:ca:56:5d
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.125 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:20 ioport:5000(size=256) memory:c8209400-c82094ff
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
root@zd8000-EC303UA-ABA:/home/frank3# ifconfig -a eth
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:ca:56:5d  
          inet addr:192.168.1.125  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:feca:565d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1749 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2308 (2.3 KB)  TX bytes:138480 (138.4 KB)

root@zd8000-EC303UA-ABA:/home/frank3# lspci -vnn | grep -A2 -e "{\0200\]" -e "[0280]"
00:00.0 Host bridge [0600]: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub [8086:2580] (rev 0e)
    Subsystem: Hewlett-Packard Company Device [103c:3082]
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=09 <?>

00:01.0 PCI bridge [0604]: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port [8086:2581] (rev 0e) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: c8100000-c81fffff
    Prefetchable memory behind bridge: d0000000-d7ffffff
    Capabilities: [88] Subsystem: Hewlett-Packard Company Device [103c:3082]
    Capabilities: [80] Power Management version 2
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [a0] Express Root Port (Slot+), MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [140] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp
--
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: a4000000-a41fffff
    Prefetchable memory behind bridge: 00000000a4200000-00000000a43fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Hewlett-Packard Company Device [103c:3082]
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel
    Capabilities: [180] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp
--
00:1d.0 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device [103c:3082]
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at 1800 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device [103c:3082]
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 38c0 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device [103c:3082]
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 38e0 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device [103c:3082]
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 3c00 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03) (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device [103c:3082]
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at c8000000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Kernel driver in use: ehci-pci

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev d3) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0b, subordinate=0d, sec-latency=32
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: c8200000-c82fffff
    Prefetchable memory behind bridge: 00000000a0000000-00000000a3ffffff
    Capabilities: [50] Subsystem: Hewlett-Packard Company Device [103c:3082]

00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:3082]
    Flags: bus master, medium devsel, latency 0, IRQ 22
    I/O ports at 3000 [size=256]
    I/O ports at 3880 [size=64]
    Memory at c8000800 (32-bit, non-prefetchable) [size=512]
    Memory at c8000400 (32-bit, non-prefetchable) [size=256]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: snd_intel8x0
    Kernel modules: snd-intel8x0

00:1e.3 Modem [0703]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller [8086:266d] (rev 03) (prog-if 00 [Generic])
    Subsystem: Hewlett-Packard Company Device [103c:3082]
    Flags: medium devsel, IRQ 22
    I/O ports at 3400 [size=256]
    I/O ports at 3800 [size=128]
    Capabilities: [50] Power Management version 2
    Kernel modules: snd-intel8x0m

00:1f.0 ISA bridge [0601]: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge [8086:2640] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:3082]
    Flags: bus master, medium devsel, latency 0
    Kernel driver in use: lpc_ich
    Kernel modules: lpc_ich, intel-rng
--
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03) (prog-if 8a [Master SecP PriP])
    Subsystem: Hewlett-Packard Company Device [103c:3082]
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 3c40 [size=16]
    Kernel driver in use: ata_piix

00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:3082]
    Flags: medium devsel, IRQ 7
    I/O ports at 3c20 [size=32]
    Kernel modules: i2c-i801

01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV380/M24 [Mobility Radeon X600] [1002:3150] (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device [103c:3082]
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at d0000000 (32-bit, prefetchable) [size=128M]
    I/O ports at 4000 [size=256]
    Memory at c8100000 (32-bit, non-prefetchable) [size=64K]
    [virtual] Expansion ROM at c8120000 [disabled] [size=128K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Express Endpoint, MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Advanced Error Reporting
    Kernel driver in use: radeon
    Kernel modules: radeon, radeonfb
--
0b:00.0 CardBus bridge [0607]: Texas Instruments PCIxx21/x515 Cardbus Controller [104c:8031]
    Subsystem: Hewlett-Packard Company Device [103c:3082]
    Flags: bus master, medium devsel, latency 168, IRQ 16
    Memory at a8000000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=0b, secondary=0c, subordinate=0c, sec-latency=176
    Memory window 0: a0000000-a3fff000 (prefetchable)
    Memory window 1: ac000000-affff000
    I/O window 0: 00005400-000054ff
    I/O window 1: 00005800-000058ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket
--
0b:00.2 FireWire (IEEE 1394) [0c00]: Texas Instruments OHCI Compliant IEEE 1394 Host Controller [104c:8032] (prog-if 10 [OHCI])
    Subsystem: Hewlett-Packard Company Device [103c:3082]
    Flags: bus master, medium devsel, latency 64, IRQ 22
    Memory at c8208000 (32-bit, non-prefetchable) [size=2K]
    Memory at c8200000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci
--
0b:00.3 Mass storage controller [0180]: Texas Instruments PCIxx21 Integrated FlashMedia Controller [104c:8033]
    Subsystem: Hewlett-Packard Company Device [103c:3082]
    Flags: bus master, medium devsel, latency 64, IRQ 16
    Memory at c8204000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: tifm_7xx1
    Kernel modules: tifm_7xx1
--
0b:00.4 SD Host controller [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller [104c:8034]
    Subsystem: Hewlett-Packard Company Device [103c:3082]
    Flags: medium devsel, IRQ 16
    Memory at c8209000 (32-bit, non-prefetchable) [size=256]
    Memory at c8208c00 (32-bit, non-prefetchable) [size=256]
    Memory at c8208800 (32-bit, non-prefetchable) [size=256]
    Capabilities: [80] Power Management version 2
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci
--
0b:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:3082]
    Flags: bus master, medium devsel, latency 64, IRQ 20
    I/O ports at 5000 [size=256]
    Memory at c8209400 (32-bit, non-prefetchable) [size=256]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp

0b:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
    Subsystem: Hewlett-Packard Company Broadcom 802.11b/g WLAN [103c:12f8]
    Flags: fast devsel, IRQ 5
    Memory at c8206000 (32-bit, non-prefetchable) [disabled] [size=8K]
    Kernel modules: ssb

---

### Post by newbie-user on 2013-08-18
Well, all you need to do is edit you /etc/network/interfaces file and add a section similar to this:

auto eth0
iface eth0 inet static
address [your static ip address]
netmask [your subnet mask]
network [your network address]
broadcast [your broadcast address]
gateway [your gateway address]
dns-nameservers [your ISP DNS servers]

---

### Post by chili555 on 2013-08-18
Please right-click the Network Manager icon and edit connections. Complete your details as here. Don't forget DNS nameservers.  [http://ubuntulinuxmint.org/wp-content/uploads/2010/09/setup-static-ip.jpg](http://ubuntulinuxmint.org/wp-content/uploads/2010/09/setup-static-ip.jpg)

We assume you want a static IP for your working ethernet and not your non-working wireless. We can get your wireless working if you want and need it.

---

### Post by chili555 on 2013-08-18
> **newbie-user said:**
> Well, all you need to do is edit you /etc/network/interfaces file and add a section similar to this:

auto eth0
iface eth0 inet static
address [your static ip address]
netmask [your subnet mask]
network [your network address]
broadcast [your broadcast address]
gateway [your gateway address]
dns-nameservers [your ISP DNS servers]This is not the preferred method if you are using Network Manager, in my opinion, because this file and Network Manager often do not work and play well together, although they are designed to do so.

---

