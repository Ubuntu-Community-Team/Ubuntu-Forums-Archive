---
title: "no internet connection Unbuntu 10.04 LTS"
date: 2012-02-26
forum: Networking &amp; Wireless
---

### Post by bergspyder on 2012-02-26
I'm running 3 PCs through 1 router:

(a) P4 XP Windows
(b) P4 Ubuntu 10.04 LTS (32-bit)
(c) Athlon II X4 640 Ubuntu 10.04 LTS (64-bit) & Windows 7 (dual boot)

(a) & (b) internet connection working perfectly (using wired connection only).

(c) internet connection works fine in Windows 7 but won't connect in Linux.

I've set all Auto eth0 network values of (c) Linux to those of (b) which is working. Also checked forums, etc., & tried several fixes but no luck so far.

Herewith lspci results:

$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc Device 68f9
01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
02:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)

Herewith \etc\udev\rules.d\70.persistent-net-rules file content (which I can't modify or delete):

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="d4:85:64:9f:fc:08", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

Can anyone help, please? 

Thanks+

---

### Post by sanderj on 2012-02-26
Post the output of these commands:

ifconfig
ping -c5 -n 8.8.8.8
mtr -r -c4 8.8.8.8

---

### Post by bergspyder on 2012-03-04
Thanks for your fast response & apologies for my late action.
Result:

bergspyder@bergspyder-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr d4:85:64:9f:fc:08  
          inet6 addr: fe80::d685:64ff:fe9f:fc08/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:3316 (3.3 KB)
          Interrupt:27 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

bergspyder@bergspyder-desktop:~$ ping -c5 -n 8.8.8.8
connect: Network is unreachable
bergspyder@bergspyder-desktop:~$ mtr -r -c4 8.8.8.8



> **sanderj said:**
> Post the output of these commands:

ifconfig
ping -c5 -n 8.8.8.8
mtr -r -c4 8.8.8.8

---

### Post by Iowan on 2012-03-04
There is no IP address for eth0. Drivers are still out of my league, but you might check:
**sudo lshw -C network**
Verify networking is enabled
Network Manager sets the interface to auto-connect

> 
Herewith \etc\udev\rules.d\70.persistent-net-rules file content (which I can't modify or delete):
**sudo** might let you edit the file.

---

### Post by sanderj on 2012-03-04
So eth0 is known. That's good. Is a ethernet cable connected to your computer? 

Ubuntu should work out-of-the-box with ethernet and DHCP. Do not edit udev files.

---

### Post by bergspyder on 2012-03-13
Hi sanderj & lowan,

Ran sudo lshw -C network. Network is disabled (see below).
As said, this is dual-boot machine and the internet connection works in Windows 7 (using same ethernet cable, same router, etc)
So why is Linux telling me network DISABLED?

Thanks again

sudo lshw -C network
[sudo] password for bergspyder: 
  *-network DISABLED      
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt3090 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:17 memory:feaf0000-feafffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 05
       serial: d4:85:64:9f:fc:08
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:27 ioport:e800(size=256) memory:febff000-febfffff memory:fdffc000-fdffffff(prefetchable)

---

### Post by sanderj on 2012-03-13
Have you already posted the output of "ifconfig" with your ethernet cable connected?


And what happens when you live-boot a Ubuntu 11.10 CD?

---

### Post by bergspyder on 2012-03-14
~$ ifconfig
eth0      Link encap:Ethernet  HWaddr d4:85:64:9f:fc:08  
          inet6 addr: fe80::d685:64ff:fe9f:fc08/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:6394 (6.3 KB)
          Interrupt:27 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

The Linux OS on this dual-boot PC was Ubuntu 11.10 (64-bit) but File Manager had no menus. From forum, it seems many users had same prob. Spent hours trying to fix it, couldn't, so reformatted with 10.04 LTS & got file manager plus all menus. If the "network disabled" problem can't be resolved, I'll try 11.10 live-boot CD but hopefully it won't come to that....

Thanks for your continuing help

---

