---
title: "Flash Video consumes all CPU resources on X220"
date: 2011-06-05
forum: Multimedia Software
---

### Post by tmalsburg on 2011-06-05
I'm running Ubuntu 11.04 (64bit) on my Thinkpad X220.  When I watch flash videos I see that Xorg consumes a lot of resources (CPU time).  Flash videos in full screen are extremely choppy.  Playing videos with Mplayer, for example, is no problem at all.  Any ideas how this can be fixed?  I found lots of posts by other people with similar problems but they had different graphics cards so their solutions were not applicable in my case.  Many thanks for any help!

uname -a:

```
Linux montana 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```

grep 'model name' /proc/cpuinfo | uniq:

```
model name	: Intel(R) Core(TM) i5-2520M CPU @ 2.50GHz
```

Here's my lspci:

```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
	Subsystem: Lenovo Device 21da
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
	Subsystem: Lenovo Device 21da
	Flags: bus master, fast devsel, latency 0, IRQ 42
	Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 5000 [size=64]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
	Subsystem: Lenovo Device 21da
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at d2525000 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>

00:16.3 Serial controller: Intel Corporation 6 Series Chipset Family KT Controller (rev 04) (prog-if 02 [16550])
	Subsystem: Lenovo Device 21da
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
	I/O ports at 50b0 [size=8]
	Memory at d252c000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: serial

00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
	Subsystem: Lenovo Device 21ce
	Flags: bus master, fast devsel, latency 0, IRQ 40
	Memory at d2500000 (32-bit, non-prefetchable) [size=128K]
	Memory at d252b000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 5080 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: e1000e
	Kernel modules: e1000e

00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])
	Subsystem: Lenovo Device 21da
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at d252a000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 04)
	Subsystem: Lenovo Device 21da
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at d2520000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b4) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 2 (rev b4) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: d2400000-d24fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 (rev b4) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=0c, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: d1c00000-d23fffff
	Prefetchable memory behind bridge: 00000000d0400000-00000000d0bfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 5 (rev b4) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0d, subordinate=0d, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: d1400000-d1bfffff
	Prefetchable memory behind bridge: 00000000d0c00000-00000000d13fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])
	Subsystem: Lenovo Device 21da
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at d2529000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation 6 Series Chipset Family LPC Controller (rev 04)
	Subsystem: Lenovo Device 21da
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 04) (prog-if 01 [AHCI 1.0])
	Subsystem: Lenovo Device 21da
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 41
	I/O ports at 50a8 [size=8]
	I/O ports at 50bc [size=4]
	I/O ports at 50a0 [size=8]
	I/O ports at 50b8 [size=4]
	I/O ports at 5060 [size=32]
	Memory at d2528000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 04)
	Subsystem: Lenovo Device 21da
	Flags: medium devsel, IRQ 11
	Memory at d2524000 (64-bit, non-prefetchable) [size=256]
	I/O ports at efa0 [size=32]
	Kernel modules: i2c-i801

03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6205 (rev 34)
	Subsystem: Intel Corporation Centrino Advanced-N 6205 AGN
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at d2400000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

0d:00.0 System peripheral: Ricoh Co Ltd Device e823 (rev 04) (prog-if 01)
	Subsystem: Lenovo Device 21da
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d1400000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci
```

---

### Post by Joe of loath on 2011-06-05
What CPU do you have? with Intel graphics, all the processing has to be done in the CPU, so speed is key.

---

### Post by tmalsburg on 2011-06-05
> **Joe of loath said:**
> What CPU do you have? with Intel graphics, all the processing has to be done in the CPU, so speed is key.

It's an Intel i5.  Should be fast enough.  Mplayer in full screen mode uses only 5% of  one core.

---

### Post by Joe of loath on 2011-06-05
Weird, I can watch anything up to and including 720p flash on my Dual Celeron T3000, although it's at nearly 100% on one core at that point.

What res. videos are you trying to watch?

---

### Post by tmalsburg on 2011-06-05
> **Joe of loath said:**
> What res. videos are you trying to watch?

The problem occurs even with small resolutions like 240p on youtube.  BTW, it's a fresh install of vanilla 11.04 without any graphics related tweaking.

---

### Post by lovinglinux on 2011-06-05
> **tmalsburg said:**
> It's an Intel i5.  Should be fast enough.  Mplayer in full screen mode uses only 5% of  one core.

Mplayer uses 5% of the CPU because it can use xv output, while flash can't.

Install [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/) and run the extension wizard. It will detect installed flash plugins, remove them and install the best option according to your system architecture and version. Additionally, it will apply some tweaks that should improve performance. 

I also develop [FlashVideoReplacer]("http://www.webgapps.org/add-ons/flashvideoreplacer"), which allows to use a plugin like gecko-mediaplayer instead of flash on popular sites like YouTube and Vimeo.

Also take a look at [http://www.webgapps.org/tutorials/firefox/optimization/flash-optimization](http://www.webgapps.org/tutorials/firefox/optimization/flash-optimization)

---

