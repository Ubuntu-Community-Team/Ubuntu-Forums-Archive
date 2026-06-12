---
title: "Internet cuts out in Karmic, Wired and Wireless"
date: 2009-11-11
forum: Networking &amp; Wireless
---

### Post by valros on 2009-11-11
In karmic, my connectivity is cutting out for up to minutes at a time at random. This is not a network problem as I am even unable to access my router or modem during these periods of no or minimal network activity.

---

### Post by SilverDrake11 on 2009-11-11
I am having a similar problem. When I boot to Karmic, my wireless keeps cutting in an out. However, when I boot to XP on the same laptop, then everything works fine again. I don't remember having this problem in Jaunty. I am running 64bit Karmic on a X61 Thinkpad.

EDIT: It seems to only happen in certain networks. For example, in my home network, I don't seem to have this problem, but my college's network, I do. When I restart, the internet works for a few minutes, then cuts out again. However, when I boot into XP, I don't have any problems like this.

---

### Post by Crafty Kisses on 2009-11-11
What kind of router do you have? Also what are the results of the following commands?
```
lspci
lsusb
lshw -C network
```

---

### Post by valros on 2009-11-12
Heres the output of those commands on my desktop, wired.

```
jonathon@jonathon-desktop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:00.0 VGA compatible controller: nVidia Corporation GT200 [GeForce GTX 260] (rev a1)
02:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
jonathon@jonathon-desktop:~$ lsusb
^[[ABus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 1532:0109 Razer USA, Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c049 Logitech, Inc. G5 Laser Mouse
jonathon@jonathon-desktop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:23:54:4c:8f:ac
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.6 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:28 ioport:e800(size=256) memory:fbfff000-fbffffff memory:f6ff0000-f6ffffff(prefetchable) memory:fbfc0000-fbfdffff(prefetchable)
jonathon@jonathon-desktop:~$ 


```

The router is a Netgear WGR614 v6, however this has been happening on public wireless networks as well.

---

### Post by valros on 2009-11-12
Silverdrake, my colleges network disconnects me often as well, have you found any reason for this?

---

### Post by valros on 2009-11-20
This is still a big problem and is getting very iritating, why at random will Karmic cut the network traffic...

---

### Post by SilverDrake11 on 2009-11-29
Still, I'm having the same problem. Now, I usually end up booting into XP when this sort of thing happens.

---

