---
title: "no hdmi option in sound settings"
date: 2012-11-25
forum: Multimedia Software
---

### Post by jon zendatta on 2012-11-25
Hi all
No volume through tv speakers via hdmi.
Am I missing an additional driver for hdmi option in sound settings? Currently Sound Settings only has * digital output (s/pdif)
                                  * speakers

---

### Post by BicyclerBoy on 2012-11-25
You probably need to post info about:
- video card
- graphics driver
- kernel version
- alsa version
- any HT amp/AVR in the loop ?
- *buntu distro 12.04 ?

If you are using a stock std distro then some of that can be guessed..

---

### Post by jon zendatta on 2012-11-26
Hi All
Ubuntu 12.04

```
lspci -v
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
	Subsystem: Acer Incorporated [ALI] Device 033e
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12) (prog-if 00 [VGA controller])
	Subsystem: Acer Incorporated [ALI] Device 033e
	Flags: bus master, fast devsel, latency 0, IRQ 41
	Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 1800 [size=8]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
	Subsystem: Acer Incorporated [ALI] Device 033e
	Flags: bus master, fast devsel, latency 0, IRQ 42
	Memory at f0804000 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: mei
	Kernel modules: mei

00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20 [EHCI])
	Subsystem: Acer Incorporated [ALI] Device 033e
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at f0806000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
	Subsystem: Acer Incorporated [ALI] Device 033e
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at f0800000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: f0400000-f04fffff
	Prefetchable memory behind bridge: 00000000f0a00000-00000000f0bfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: f0500000-f05fffff
	Prefetchable memory behind bridge: 000000007c000000-000000007c1fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20 [EHCI])
	Subsystem: Acer Incorporated [ALI] Device 033e
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f0807000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0f, subordinate=0f, sec-latency=0
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
	Subsystem: Acer Incorporated [ALI] Device 033e
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05) (prog-if 01 [AHCI 1.0])
	Subsystem: Acer Incorporated [ALI] Device 033e
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 40
	I/O ports at 1818 [size=8]
	I/O ports at 180c [size=4]
	I/O ports at 1810 [size=8]
	I/O ports at 1808 [size=4]
	I/O ports at 1820 [size=32]
	Memory at f0808000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
	Subsystem: Acer Incorporated [ALI] Device 033e
	Flags: medium devsel, IRQ 10
	Memory at f0809000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 1840 [size=32]
	Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
	Subsystem: Acer Incorporated [ALI] Device 033e
	Flags: fast devsel, IRQ 18
	Memory at f080a000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: intel ips
	Kernel modules: intel_ips

02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
	Subsystem: Acer Incorporated [ALI] Aspire 7740G
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at f0400000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: tg3
	Kernel modules: tg3

04:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Foxconn International, Inc. T77H047.31 802.11bgn Wireless Half-size Mini PCIe Card [AR9283]
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f0500000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0
```
I cannot test on TV for several hours. In Alsamixer -> Intel IbexPeak HDMID
Line     muted
Mic      muted
Beep     muted
Internal muted
Which should I unmute? Or is there more information I can give?
Thanks for the help:KS

---

### Post by BicyclerBoy on 2012-11-26
*buntu takes a conservative approach to the newer intel iCPU/iGFX..
It defaults to a no h/w acceleration & an old intel driver.
This also impacts on the HDMI audio functionality.

In a terminal:
aplay -l

You could try install/run "pavucontrol". Check out the configuration & then output tabs..
Pulse audio is the system wide audio server in ubuntu.
Post your finding ...

IMO to get the best from the later iCPU/iGPU need a later kernel & intel driver (i915/i965) from xorg-edgers ppa.
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

The xorg-edgers ppa is under consistent development & can be unstable. Could be tricky to un-install/remove..
The VA-API stuff prob won't work without xorg-edgers..

To get h/w video decode working (VA-API) install:
i965-va-driver
libva-intel-vaapi-driver

There are gstreamer vaapi plugins if you use that..

VLC & mplayer (& mythtv, XBMC) have VA-API support.

---

### Post by jon zendatta on 2012-11-30
BicyclerBoy thanks for help:KS

---

