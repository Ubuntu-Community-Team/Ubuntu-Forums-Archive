---
title: "No HMDI video (or sound) from Ubuntu 12.10 to Sony Bravia TV"
date: 2012-12-01
forum: Multimedia Software
---

### Post by ob3ron on 2012-12-01
I just wiped Win7 and installed Ubuntu 12.10 on the laptop that I use as an HTPC. After I got everything set up, I plugged in my HDMI cable and went to Displays to try to turn on HDMI. No luck! Only my laptop is listed when I have HDMI connected.

xrandr doesn't see that the TV is connected. And when I go to Sound, it doesn't show any options for HDMI. 

The TV is circa 2009-2010. Could it be an issue with the EDID?


```
xrandr --verbose
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
LVDS1 connected 1366x768+0+0 (0x8f) normal (normal left inverted right x axis y axis) 309mm x 174mm
	Identifier: 0x8a
	Timestamp:  11487666
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
		00ffffffffffff0025cc140000000000
		00140103801f12780a87f594574f8c27
		27505400000001010101010101010101
		010101010101bc1b5684500016303020
		140035ae10000018bc1b568450001630
		3020140035ae10000000000000fe0048
		52315654803134304757303100000000
		00000000000000000001010a2020004b
	BACKLIGHT: 15 (0x0000000f)	range:  (0,15)
	Backlight: 15 (0x0000000f)	range:  (0,15)
	scaling mode:	Full aspect
		supported: None         Full         Center       Full aspect 
  1366x768 (0x8f)   71.0MHz -HSync -VSync *current +preferred
        h: width  1366 start 1414 end 1446 total 1498 skew    0 clock   47.4KHz
        v: height  768 start  769 end  773 total  790           clock   60.0Hz
  1360x768 (0x90)   84.8MHz -HSync +VSync
        h: width  1360 start 1432 end 1568 total 1776 skew    0 clock   47.7KHz
        v: height  768 start  771 end  781 total  798           clock   59.8Hz
  1360x768 (0x91)   72.0MHz +HSync -VSync
        h: width  1360 start 1408 end 1440 total 1520 skew    0 clock   47.4KHz
        v: height  768 start  771 end  781 total  790           clock   60.0Hz
  1024x768 (0x64)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x65)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  800x600 (0x66)   36.0MHz +HSync +VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock   35.2KHz
        v: height  600 start  601 end  603 total  625           clock   56.2Hz
  640x480 (0x92)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
VGA1 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x8b
	Timestamp:  11487666
	Subpixel:   unknown
	Clones:    
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
HDMI1 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x8c
	Timestamp:  11487666
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
		supported: force-dvi    off          auto         on          
DP1 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x8d
	Timestamp:  11487666
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
		supported: force-dvi    off          auto         on   
```

Here's my lspci output

```
lspci -v
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
	Subsystem: Intel Corporation Core Processor DRAM Controller
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel

00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 18) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: f9000000-fa0fffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000d1ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18) (prog-if 00 [VGA controller])
	Subsystem: Dell Device 0468
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at fa400000 (64-bit, non-prefetchable) [size=4M]
	Memory at b0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at f080 [size=8]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
	Subsystem: Dell Device 0468
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at fb309000 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: mei
	Kernel modules: mei

00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) (prog-if 20 [EHCI])
	Subsystem: Dell Device 0468
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at fb308000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
	Subsystem: Dell Device 0468
	Flags: bus master, fast devsel, latency 0, IRQ 47
	Memory at fb300000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=11, subordinate=11, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=12, subordinate=12, sec-latency=0
	Memory behind bridge: fb200000-fb2fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=14, subordinate=14, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fa800000-fb1fffff
	Prefetchable memory behind bridge: 00000000d2100000-00000000d2afffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=16, subordinate=16, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Prefetchable memory behind bridge: 00000000d2c00000-00000000d2cfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) (prog-if 20 [EHCI])
	Subsystem: Dell Device 0468
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at fb307000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=20, subordinate=20, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
	Subsystem: Dell Device 0468
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: lpc_ich

00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06) (prog-if 01 [AHCI 1.0])
	Subsystem: Dell Device 0468
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 42
	I/O ports at f070 [size=8]
	I/O ports at f060 [size=4]
	I/O ports at f050 [size=8]
	I/O ports at f040 [size=4]
	I/O ports at f020 [size=32]
	Memory at fb306000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
	Subsystem: Dell Device 0468
	Flags: medium devsel, IRQ 4
	Memory at fb305000 (64-bit, non-prefetchable) [size=256]
	I/O ports at f000 [size=32]
	Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
	Subsystem: Dell Device 0468
	Flags: fast devsel, IRQ 18
	Memory at fb304000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel modules: intel_ips

01:00.0 VGA compatible controller: NVIDIA Corporation Device 0df1 (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Dell Device 0468
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f9000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at d0000000 (64-bit, prefetchable) [size=32M]
	I/O ports at e000 [size=128]
	Expansion ROM at fa000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nouveau
	Kernel modules: nouveau, nvidiafb

12:00.0 Network controller: Intel Corporation Centrino Advanced-N 6200 (rev 35)
	Subsystem: Intel Corporation Centrino Advanced-N 6200 2x2 AGN
	Flags: bus master, fast devsel, latency 0, IRQ 46
	Memory at fb200000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlwifi
	Kernel modules: iwlwifi

14:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 30)
	Subsystem: Dell Device 0468
	Physical Slot: 3
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at fa803000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

14:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 30) (prog-if 01)
	Subsystem: Dell Device 0468
	Physical Slot: 3
	Flags: fast devsel, IRQ 19
	Memory at fa802000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel modules: sdhci-pci

14:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 30)
	Subsystem: Dell Device 0468
	Physical Slot: 3
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at fa801000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: jmb38x_ms
	Kernel modules: jmb38x_ms

14:00.4 System peripheral: JMicron Technology Corp. xD Host Controller (rev 30)
	Subsystem: Dell Device 0468
	Physical Slot: 3
	Flags: bus master, fast devsel, latency 0, IRQ 3
	Memory at fa800000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

16:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
	Subsystem: Dell Device 0468
	Flags: bus master, fast devsel, latency 0, IRQ 43
	I/O ports at c000 [size=256]
	Memory at d2c04000 (64-bit, prefetchable) [size=4K]
	Memory at d2c00000 (64-bit, prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

```

I'm not sure why there are two VGA controllers listed...
> 
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18) (prog-if 00 [VGA controller])
	Subsystem: Dell Device 0468
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at fa400000 (64-bit, non-prefetchable) [size=4M]
	Memory at b0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at f080 [size=8]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

01:00.0 VGA compatible controller: NVIDIA Corporation Device 0df1 (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Dell Device 0468
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f9000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at d0000000 (64-bit, prefetchable) [size=32M]
	I/O ports at e000 [size=128]
	Expansion ROM at fa000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nouveau
	Kernel modules: nouveau, nvidiafb

---

### Post by papibe on 2012-12-01
Hi ob3ron. Welcome to the forums ):P

Your laptop has [Nvidia Optimus]("http://www.nvidia.com/object/optimus_technology.html"). Which is a kind of new graphic architecture and it's just starting to be supported on Linux. Despite that fact, there are a couple of projects in progress that have some success to support it.

I would advice you to start reading a couple of useful threads. [This]("http://ubuntuforums.org/showthread.php?t=1657660") one to understand what it is (but a pessimist). And this [other]("http://ubuntuforums.org/showthread.php?t=1845896&highlight=nvidia") one (from post #7), with a more practical approach.

There are laptops that have the ability to select the graphics from the BIOS. Some only allow you to disable the discrete card, but others even let you select either integrated (Intel), discrete (just the Nvidia card, which would be better ), or NVIDIA Optimus.

If you are able to make it work, I would take the following procedure to install the Nvidia driver:

First I would try the suggested driver. Go to 'additional drivers' or 'hardware drivers' and install the suggested driver.

If that doesn't work I would upgrade to the version of this ppa:
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
```

Then if that doesn't work either, there's another ppa with bleeding-edge versions:
 
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```

I would let the driver from the Nvidia site as the last resort.

I hope that helps. Let us know how it goes.
Regards.

---

### Post by ob3ron on 2012-12-01
Hi papibe, 

Thanks so much for your response. I didn't even realise my laptop had Nvidia Optimus!

Just a quick update: I checked my BIOS to see if I could enable/disable the integrated. No luck. I'll see if there are any BIOS updates I could apply.

Thanks kindly

---

