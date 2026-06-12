---
title: "NO video on Sony Bravia via HDMI"
date: 2013-08-17
forum: Multimedia Software
---

### Post by jon-zendatta on 2013-08-17
Hi all.
I have a clean 12.04 install. No picture on my Sony Bravia via HDMI. Any ideas please:KS

```
xrandr --verbose
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
LVDS1 connected 1366x768+0+0 (0x45) normal (normal left inverted right x axis y axis) 344mm x 193mm
	Identifier: 0x41
	Timestamp:  21765908
	Subpixel:   horizontal rgb
	Gamma:      1.0:1.0:1.0
	Brightness: 1.0
	Clones:    
	CRTC:       0
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	EDID:
		00ffffffffffff0006afec2200000000
		01130103802213780ac8959e57549226
		0f505400000001010101010101010101
		010101010101121b5642500026302018
		340058c1100000180000000f00000000
		00000000000000000020000000fe0041
		554f0a202020202020202020000000fe
		004231353658573032205632200a00c0
	BACKLIGHT: 0 (0x00000000)	range:  (0,9)
	Backlight: 0 (0x00000000)	range:  (0,9)
	scaling mode:	Full aspect
		supported: None         Full         Center       Full aspect 
  1366x768 (0x45)   69.3MHz -HSync -VSync *current +preferred
        h: width  1366 start 1398 end 1422 total 1432 skew    0 clock   48.4KHz
        v: height  768 start  771 end  775 total  806           clock   60.0Hz
  1360x768 (0x46)   84.8MHz -HSync +VSync
        h: width  1360 start 1432 end 1568 total 1776 skew    0 clock   47.7KHz
        v: height  768 start  771 end  781 total  798           clock   59.8Hz
  1360x768 (0x47)   72.0MHz +HSync -VSync
        h: width  1360 start 1408 end 1440 total 1520 skew    0 clock   47.4KHz
        v: height  768 start  771 end  781 total  790           clock   60.0Hz
  1024x768 (0x48)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x49)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  800x600 (0x4a)   36.0MHz +HSync +VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock   35.2KHz
        v: height  600 start  601 end  603 total  625           clock   56.2Hz
  640x480 (0x4b)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
VGA1 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x42
	Timestamp:  21765908
	Subpixel:   unknown
	Clones:    
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
HDMI1 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x43
	Timestamp:  21765908
	Subpixel:   unknown
	Clones:    
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	Broadcast RGB:	Full
		supported: Full         Limited 16:2
	audio:	auto
		supported: off          auto         on          
DP1 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x44
	Timestamp:  21765908
	Subpixel:   unknown
	Clones:    
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	Broadcast RGB:	Full
		supported: Full         Limited 16:2
	audio:	auto
		supported: off          auto         on

```
```
lspci -v
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
	Subsystem: Acer Incorporated [ALI] Device 033e
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel


00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12) (prog-if 00 [VGA controller])
	Subsystem: Acer Incorporated [ALI] Device 033e
	Flags: bus master, fast devsel, latency 0, IRQ 42
	Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 1800 [size=8]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915


00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
	Subsystem: Acer Incorporated [ALI] Device 033e
	Flags: bus master, fast devsel, latency 0, IRQ 41
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

---

### Post by jon-zendatta on 2013-08-22
Still no picture, the movie player doesn't even display on tv although I do get the audio and all that is displayed on the tv is my laptop Desktop. On my previous install of 12.04, HDMI worked fine, same tv & laptop.
Any more ideas?:KS

---

