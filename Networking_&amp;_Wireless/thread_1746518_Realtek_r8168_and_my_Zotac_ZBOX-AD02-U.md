---
title: "Realtek r8168 and my Zotac ZBOX-AD02-U"
date: 2011-05-01
forum: Networking &amp; Wireless
---

### Post by Starmartyr on 2011-05-01
I have built my ZBOX-AD02-U with 4gRam and 320g harddrive, and am using it atm to type this.  So, wired works.  But, I need wireless to work, as the box will be in my livingroom.  

I installed both Ubuntu 10.10 32-bit and 11.04 64 bit with no success with the r8168 Wifi.  It shows it is connected to my network, but it does no load anything.  I have researched the Ubuntu forums and thought I would find an answer, but have had no success.  

I need to know if there is a way to get this to work, or have this disabled somehow so that I can get a wireless connection to my router.  

lspci = 
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] Pavilion DM1Z-3000 Host bridge
00:01.0 VGA compatible controller: ATI Technologies Inc Device 9802
00:01.1 Audio device: ATI Technologies Inc Device 1314
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Device 1512
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] (rev 40)
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:15.0 PCI bridge: ATI Technologies Inc Device 43a0
00:15.2 PCI bridge: ATI Technologies Inc Device 43a2
00:15.3 PCI bridge: ATI Technologies Inc Device 43a3
00:16.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
03:00.0 Network controller: Ralink corp. RT2860
06:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

```

modinfo r8168 = 
```
filename:       /lib/modules/2.6.38-8-generic/kernel/drivers/net/r8168.ko
version:        8.023.00-NAPI
license:        GPL
description:    RealTek RTL-8168 Gigabit Ethernet driver
author:         Realtek and the Linux r8168 crew <netdev@vger.kernel.org>
srcversion:     8234C7235B5D2A2B5E41CB6
alias:          pci:v000010ECd00008168sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.38-8-generic SMP mod_unload modversions 
parm:           eee_enable:int
parm:           speed:force phy operation. Deprecated by ethtool (8). (array of int)
parm:           duplex:force phy operation. Deprecated by ethtool (8). (array of int)
parm:           autoneg:force phy operation. Deprecated by ethtool (8). (array of int)
parm:           rx_copybreak:Copy breakpoint for copy-only-tiny-frames (int)
parm:           use_dac:Enable PCI DAC. Unsafe on 32 bit PCI slot. (int)
parm:           debug:Debug verbosity level (0=none, ..., 16=all) (int)

```

Any help with be greatly appreciated.

---

### Post by chili555 on 2011-05-02
> no success with the r8168 Wifi.r8168 is the driver for your wired ethernet. It has nothing to do with wireless. I believe the driver for your wireless is rt2860sta. Sometimes there is a conflicting driver that also loads, rt2800pci. Let's check:```
lsmod | grep rt2
lspci -nn | grep Network
```Thanks.

---

