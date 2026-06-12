---
title: "[Announcement] PianoBooster version 0.5.0 has been released"
date: 2008-12-03
forum: Multimedia Software
---

### Post by louis_b on 2008-12-03
PianoBooster version 0.5.0 has been released, this is the first ever
release of PianoBooster.

Piano Booster is a MIDI file player that displays the musical score
AND teaches you how to play the piano.

To see what it is all about take a look at the screen shot:

[http://pianobooster.sourceforge.net/images/LinuxScreenShot.png](http://pianobooster.sourceforge.net/images/LinuxScreenShot.png)


You can watch a video of it in action on YouTube:

[http://uk.youtube.com/watch?v=7YaDllVreuM](http://uk.youtube.com/watch?v=7YaDllVreuM)

Piano Booster 0.5.0 is released under the GPL and is available at
SourceForge on this page:

[http://pianobooster.sourceforge.net](http://pianobooster.sourceforge.net)


L o u i s    B a r m a n

---

### Post by NoBugs! on 2009-10-28
Looks good. Is there any way to use a real piano near the computer microphone instead of using a midi-keyboard?

---

### Post by louis_b on 2009-10-29
> **NoBugs! said:**
> Looks good. Is there any way to use a real piano near the computer microphone instead of using a midi-keyboard?

Sorry it is unlikely to work with a real piano. However it may work with just playing a single note at time using (monophonic) real-time pitch tracking (see: [http://aubio.org/](http://aubio.org/) and <http://aubio.org/aubiopitch.html> and  Rakarrack) but I have not tried it with these programs. Midi keyboards are not too expensive.

---

### Post by svenskmand on 2010-06-12
[I just installed piano booster through this ppa]("https://launchpad.net/~racb/+archive/extra") but when I try to start it with the command pianobooster the program window does not show up :(, what is wrong?

---

### Post by louis_b on 2010-06-12
Please try typing pianobooster in a terminal and copy and paste the results here.

Are you using 32 or 64 bit ubuntu? And what version of Ubuntu are you using? Finally please give details of your graphics card.

Thanks

Louis

---

### Post by svenskmand on 2010-06-12
When I run the command pianobooster from a terminal nothing is printet and the program window does not show up, I have both with a JACK server running, with no server running, does PianoBooster use JACK?. I have 64-bit lucid and a ATI Mobility Radeon HD 3450 graphics card and [the computer is a HP Pavilion dv7-1190eo]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01589469&tmp_task=prodinfoCategory&lc=en&dlc=da&cc=dk&lang=da&product=3826583"). Here is the output of lspci -v
```

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, 66MHz, medium devsel, latency 0
	Capabilities: <access denied>

00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00007000-00007fff
	Memory behind bridge: d2400000-d24fffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=07, sec-latency=0
	I/O behind bridge: 00003000-00006fff
	Memory behind bridge: d1400000-d23fffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000d0ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	Memory behind bridge: d1300000-d13fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	Memory behind bridge: d1200000-d12fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d1100000-d11fffff
	Prefetchable memory behind bridge: 00000000d1000000-00000000d10fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] (prog-if 01)
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at 8038 [size=8]
	I/O ports at 804c [size=4]
	I/O ports at 8030 [size=8]
	I/O ports at 8048 [size=4]
	I/O ports at 8010 [size=16]
	Memory at d2508000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at d2507000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at d2506000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at d2508500 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at d2505000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at d2504000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at d2508400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: 66MHz, medium devsel
	Capabilities: <access denied>
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (prog-if 8a [Master SecP PriP])
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 8000 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at d2500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=80, subordinate=8f, sec-latency=64
	I/O behind bridge: 00001000-00001fff

00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
	Flags: fast devsel
	Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>

00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
	Flags: fast devsel

01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, fast devsel, latency 0, IRQ 31
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 7000 [size=256]
	Memory at d2400000 (32-bit, non-prefetchable) [size=64K]
	Expansion ROM at d2420000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx, radeon

01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at d2410000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

08:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at d1300000 (32-bit, non-prefetchable) [size=2K]
	Memory at d1300d00 (32-bit, non-prefetchable) [size=128]
	Memory at d1300c80 (32-bit, non-prefetchable) [size=128]
	Memory at d1300c00 (32-bit, non-prefetchable) [size=128]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

08:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at d1300b00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

08:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (prog-if 01)
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: fast devsel, IRQ 17
	Memory at d1300a00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel modules: sdhci-pci

08:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at d1300900 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: jmb38x_ms
	Kernel modules: jmb38x_ms

08:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, fast devsel, latency 0, IRQ 5
	Memory at d1300800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

09:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Device 137b
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at d1200000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath5k
	Kernel modules: ath5k

0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, fast devsel, latency 0, IRQ 30
	I/O ports at 2000 [size=256]
	Memory at d1100000 (64-bit, non-prefetchable) [size=4K]
	Memory at d1000000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at d1020000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

```
Do you need anything more?

---

