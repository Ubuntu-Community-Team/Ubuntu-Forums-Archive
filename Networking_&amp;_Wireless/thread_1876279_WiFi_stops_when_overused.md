---
title: "WiFi stops when overused"
date: 2011-11-05
forum: Networking &amp; Wireless
---

### Post by Daneel.Olivaw on 2011-11-05
I'm on Ubuntu 11.04 and every time I "overuse" my WiFi connection it stops. By "overuse" I mean using torrent, downloading large programs via the Software Centre or transferring large files between computers over LAN network; and by "stops" I mean that it doesn't appear to be disconnected but it doesn't work. When just surfing on the internet or even downloading files it works perfectly. 
I'm pretty sure this doesn't happen on my Windows install so it should be a software issue. 

I don't know what information could be useful. Just tell me what commands to type and paste and I'll do it :)

Thanks!

---

### Post by bluexrider on 2011-11-05
You didn't mention what wifi you have. 

Please post the output of
 	Code:
 	lspci -vnn | grep -a4 -i net lsmod

---

### Post by Daneel.Olivaw on 2011-11-05
Sorry.

Here's the output of lspci -vnn

```
daneel@daneel-Aspire-5536:~$ lspci -vnn
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS780 Host Bridge [1022:9600]
	Subsystem: Acer Incorporated [ALI] Device [1025:0206]
	Flags: bus master, 66MHz, medium devsel, latency 64
	Capabilities: <access denied>

00:01.0 PCI bridge [0604]: Acer Incorporated [ALI] Device [1025:9602] (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 66
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: cfd00000-cfefffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel modules: shpchp

00:04.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0) [1022:9604] (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: f0300000-f03fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1) [1022:9605] (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	Memory behind bridge: f0400000-f04fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:11.0 SATA controller [0106]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] [1002:4390] (prog-if 01 [AHCI 1.0])
	Subsystem: Acer Incorporated [ALI] Device [1025:0206]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at 8420 [size=8]
	I/O ports at 8414 [size=4]
	I/O ports at 8418 [size=8]
	I/O ports at 8410 [size=4]
	I/O ports at 8400 [size=16]
	Memory at f0208000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:12.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397] (prog-if 10 [OHCI])
	Subsystem: Acer Incorporated [ALI] Device [1025:0206]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at f0004000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.1 USB Controller [0c03]: ATI Technologies Inc SB7x0 USB OHCI1 Controller [1002:4398] (prog-if 10 [OHCI])
	Subsystem: Acer Incorporated [ALI] Device [1025:0206]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at f0005000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396] (prog-if 20 [EHCI])
	Subsystem: Acer Incorporated [ALI] Device [1025:0206]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at f0208400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:13.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397] (prog-if 10 [OHCI])
	Subsystem: Acer Incorporated [ALI] Device [1025:0206]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at f0006000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.1 USB Controller [0c03]: ATI Technologies Inc SB7x0 USB OHCI1 Controller [1002:4398] (prog-if 10 [OHCI])
	Subsystem: Acer Incorporated [ALI] Device [1025:0206]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at f0007000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396] (prog-if 20 [EHCI])
	Subsystem: Acer Incorporated [ALI] Device [1025:0206]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at f0208800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 3a)
	Subsystem: Acer Incorporated [ALI] Device [1025:0206]
	Flags: 66MHz, medium devsel
	Capabilities: <access denied>
	Kernel driver in use: piix4_smbus
	Kernel modules: sp5100_tco, i2c-piix4

00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
	Subsystem: Acer Incorporated [ALI] Device [1025:0206]
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at f0000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge [0601]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d]
	Subsystem: Acer Incorporated [ALI] Device [1025:0206]
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384] (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=64

00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration [1022:1300] (rev 40)
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Processor Address Map [1022:1301]
	Flags: fast devsel

00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller [1022:1302]
	Flags: fast devsel

00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control [1022:1303]
	Flags: fast devsel
	Capabilities: <access denied>
	Kernel driver in use: k10temp
	Kernel modules: k10temp

00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Processor Link Control [1022:1304]
	Flags: fast devsel

01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics] [1002:9612] (prog-if 00 [VGA controller])
	Subsystem: Acer Incorporated [ALI] Device [1025:0206]
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 9000 [size=256]
	Memory at cfdf0000 (32-bit, non-prefetchable) [size=64K]
	Memory at cfe00000 (32-bit, non-prefetchable) [size=1M]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: radeon
	Kernel modules: radeon

01:05.1 Audio device [0403]: ATI Technologies Inc RS780 Azalia controller [1002:960f]
	Subsystem: Acer Incorporated [ALI] Device [1025:0206]
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at cfdec000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

03:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
	Subsystem: Acer Incorporated [ALI] Device [1025:0207]
	Flags: bus master, fast devsel, latency 0, IRQ 42
	Memory at f0300000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: tg3
	Kernel modules: tg3

06:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
	Subsystem: Lite-On Communications Inc Device [11ad:6600]
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f0400000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k


```

The important be must be that last one. 


grep -a4 -i net lsmod returns: "grep: lsmod: No such file or directory"

---

### Post by bluexrider on 2011-11-06
Seams there are some issues with this and the kernel and has been going on for a while.


Basically using the backports to get the correct driver. 



sudo apt-get install linux-modules-backports-natty

sudo apt-get update
sudo apt get upgrade

---

### Post by Daneel.Olivaw on 2011-11-06
Thanks. Glad to know it's a known problem with a solution. But I don't seem to find linux-modules-backports-natty on the repository (sudo apt-get install is "unable to locate" the package and so do I). Searching through the Software Centre I find lots of versions but I have absolutely no idea which is the appropriate one. Here's a screencap to get an idea [http://i.imgur.com/VlGAq.png](http://i.imgur.com/VlGAq.png). 

I did find that I should uncomment some repositories from my sources.list. I did. 
I guess I should install linux-backports-modules-net-natty-generic and linux-backports-modules-headears-natty-generic, it's that ok? I have no idea whatsoever of what I'm doing and I don't want my laptop to explode into pieces.

---

### Post by bluexrider on 2011-11-06
Go ahead and do what your doing. I don't think you need a fire extinguisher yet.

Search for Linux Backports modules version 2.6.38.xx 

xx is whatever kernel you are running.

I would also pick any wireless drivers for your kernel image too.

---

