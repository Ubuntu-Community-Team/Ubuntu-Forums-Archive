---
title: "Relatively low volume"
date: 2009-07-21
forum: Multimedia Software
---

### Post by ivanko.rus on 2009-07-21
Hello! I have a little problem (not critical), the volume in my Ubuntu is lower, than in, for example, Windows (which is also installed on my machine). It's high enough to listen to the music, but I'd like it to be a bit louder. I tried amplifying the volume of the audio files, but some frequencies become like "noisy" or something. I tried recompiling the realtek driver, but it didn't give any results. All the volume levels in gnome-mixer and in alsamixer are set to their maximum.
Here is my lspci -v output:
```
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
    Subsystem: Giga-byte Technology Device 5000
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information <?>
    Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: e4000000-e7ffffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000dfffffff
    Capabilities: [88] Subsystem: Giga-byte Technology Device 5000
    Capabilities: [80] Power Management version 3
    Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [a0] Express Root Port (Slot+), MSI 00
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [140] Root Complex Link <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at e100 [size=32]
    Capabilities: [50] PCIe advanced features <?>
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at e200 [size=32]
    Capabilities: [50] PCIe advanced features <?>
    Kernel driver in use: uhci_hcd

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at e000 [size=32]
    Capabilities: [50] PCIe advanced features <?>
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20)
    Subsystem: Giga-byte Technology Device 5006
    Flags: bus master, medium devsel, latency 0, IRQ 18
    Memory at eb004000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCIe advanced features <?>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
    Subsystem: Giga-byte Technology Device a002
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at eb000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [130] Root Complex Link <?>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00009000-00009fff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [90] Subsystem: Giga-byte Technology Device 5001
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [180] Root Complex Link <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: e8000000-e8ffffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [90] Subsystem: Giga-byte Technology Device 5001
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [180] Root Complex Link <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: e9000000-eaffffff
    Prefetchable memory behind bridge: 0000000080000000-00000000800fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [90] Subsystem: Giga-byte Technology Device 5001
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [180] Root Complex Link <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at e300 [size=32]
    Capabilities: [50] PCIe advanced features <?>
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at e400 [size=32]
    Capabilities: [50] PCIe advanced features <?>
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at e500 [size=32]
    Capabilities: [50] PCIe advanced features <?>
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20)
    Subsystem: Giga-byte Technology Device 5006
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at eb005000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCIe advanced features <?>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
    I/O behind bridge: 0000a000-0000afff
    Capabilities: [50] Subsystem: Giga-byte Technology Device 5000

00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
    Subsystem: Giga-byte Technology Device 5001
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information <?>
    Kernel modules: iTCO_wdt

00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
    Subsystem: Giga-byte Technology Device b002
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at f000 [size=16]
    I/O ports at fc00 [size=16]
    Capabilities: [70] Power Management version 3
    Capabilities: [b0] PCIe advanced features <?>
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
    Subsystem: Giga-byte Technology Device 5001
    Flags: medium devsel, IRQ 3
    Memory at eb006000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 0500 [size=32]
    Kernel modules: i2c-i801

00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02) (prog-if 85 [Master SecO PriO])
    Subsystem: Giga-byte Technology Device b002
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at e700 [size=8]
    I/O ports at e800 [size=4]
    I/O ports at e900 [size=8]
    I/O ports at ea00 [size=4]
    I/O ports at eb00 [size=16]
    I/O ports at ec00 [size=16]
    Capabilities: [70] Power Management version 3
    Capabilities: [b0] PCIe advanced features <?>
    Kernel driver in use: ata_piix

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GS (rev a2)
    Subsystem: XFX Pine Group Inc. Device 2335
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at e6000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=512M]
    Memory at e4000000 (64-bit, non-prefetchable) [size=32M]
    I/O ports at b000 [size=128]
    [virtual] Expansion ROM at e7000000 [disabled] [size=128K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information <?>
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nvidiafb

03:00.0 IDE interface: JMicron Technologies, Inc. JMB368 IDE controller (prog-if 85 [Master SecO PriO])
    Subsystem: Giga-byte Technology Device b000
    Flags: bus master, fast devsel, latency 0, IRQ 19
    I/O ports at c000 [size=8]
    I/O ports at c100 [size=4]
    I/O ports at c200 [size=8]
    I/O ports at c300 [size=4]
    I/O ports at c400 [size=16]
    Capabilities: [68] Power Management version 2
    Capabilities: [50] Express Legacy Endpoint, MSI 01
    Capabilities: [70] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Kernel driver in use: pata_jmicron

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
    Subsystem: Giga-byte Technology Device e000
    Flags: bus master, fast devsel, latency 0, IRQ 2299
    I/O ports at d000 [size=256]
    Memory at ea000000 (64-bit, non-prefetchable) [size=4K]
    [virtual] Expansion ROM at 80000000 [disabled] [size=128K]
    Capabilities: [40] Power Management version 2
    Capabilities: [48] Vital Product Data <?>
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
    Capabilities: [60] Express Endpoint, MSI 00
    Capabilities: [84] Vendor Specific Information <?>
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [12c] Virtual Channel <?>
    Capabilities: [148] Device Serial Number 68-81-ec-10-00-00-00-00
    Capabilities: [154] Power Budgeting <?>
    Kernel driver in use: r8169
    Kernel modules: r8169

```My motherboard model is GA-P35-DS3L and I'm using the onboard audio which is ALC888. So this is what I got :D.

I would appreciate any help! Thanks in advance! ;)

---

### Post by igorzwx on 2009-07-21
Hi Ivanko!

Install another Ubuntu in dual boot.
try:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
[http://wiki.archlinux.org/index.php/OSS](http://wiki.archlinux.org/index.php/OSS)

Best,
igor

---

### Post by ivanko.rus on 2009-07-21
Thanks for your help, igor! But the volume is still the same :(

---

### Post by igorzwx on 2009-07-21
if you have oss4

try

osstest

ossxmix

---

### Post by ikt on 2009-07-21
I have the exact same audio chipset and I have the exact same problem.


```

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
	Subsystem: Giga-byte Technology Device 5000
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: ec000000-efffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
	Subsystem: Giga-byte Technology Device 5004
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at e000 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
	Subsystem: Giga-byte Technology Device 5004
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at e100 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
	Subsystem: Giga-byte Technology Device 5004
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at e500 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20)
	Subsystem: Giga-byte Technology Device 5006
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at f2105000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
	Subsystem: Giga-byte Technology Device a002
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f2100000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: f2000000-f20fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: f0000000-f1ffffff
	Prefetchable memory behind bridge: 00000000f2200000-00000000f22fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
	Subsystem: Giga-byte Technology Device 5004
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at e200 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
	Subsystem: Giga-byte Technology Device 5004
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at e300 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
	Subsystem: Giga-byte Technology Device 5004
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at e400 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20)
	Subsystem: Giga-byte Technology Device 5006
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f2104000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: e4000000-ebffffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
	Subsystem: Giga-byte Technology Device 5001
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Giga-byte Technology Device b002
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at f000 [size=16]
	I/O ports at fc00 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
	Subsystem: Giga-byte Technology Device 5001
	Flags: medium devsel, IRQ 9
	Memory at f2106000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 0500 [size=32]
	Kernel modules: i2c-i801

00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02) (prog-if 85 [Master SecO PriO])
	Subsystem: Giga-byte Technology Device b002
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at e700 [size=8]
	I/O ports at e800 [size=4]
	I/O ports at e900 [size=8]
	I/O ports at ea00 [size=4]
	I/O ports at eb00 [size=16]
	I/O ports at ec00 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix

01:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTS] (rev a2)
	Subsystem: LeadTek Research Inc. Device 2ab2
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at ee000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at ec000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at a000 [size=128]
	[virtual] Expansion ROM at ef000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02) (prog-if 01)
	Subsystem: Giga-byte Technology Device b000
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f2000000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02) (prog-if 85 [Master SecO PriO])
	Subsystem: Giga-byte Technology Device b000
	Flags: bus master, fast devsel, latency 0, IRQ 17
	I/O ports at b000 [size=8]
	I/O ports at b100 [size=4]
	I/O ports at b200 [size=8]
	I/O ports at b300 [size=4]
	I/O ports at b400 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_jmicron

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
	Subsystem: Giga-byte Technology Device e000
	Flags: bus master, fast devsel, latency 0, IRQ 2299
	I/O ports at c000 [size=256]
	Memory at f1000000 (64-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at f2200000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

05:01.0 Multimedia audio controller: Creative Labs SB X-Fi
	Subsystem: Creative Labs Device 0021
	Flags: bus master, medium devsel, latency 32, IRQ 11
	I/O ports at d000 [size=32]
	Memory at e8000000 (64-bit, non-prefetchable) [size=2M]
	Memory at e4000000 (64-bit, non-prefetchable) [size=64M]
	Capabilities: <access denied>

05:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10)
	Subsystem: Giga-byte Technology Device 1000
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at e8204000 (32-bit, non-prefetchable) [size=2K]
	Memory at e8200000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

```



> **igorzwx said:**
> if you have oss4

try

osstest

ossxmix


This doesn't mean anything to me :s

---

### Post by igorzwx on 2009-07-21
I should not mean anything, if you have not OSS4 installed?

---

### Post by ivanko.rus on 2009-07-21
OK, when I installed OSS4, I followed all the steps of the how-to (including the ossxmix), but the volume level was the same. Now I reverted to alsa + pulseaudio again (just to be sure), and there is no difference. Also I followed some guides on configuring the PulseAudio and added the "model=6stack-dig" into the "options hda-snd-intel" in the alsa-base.conf file. No results. That's really strange :confused:

---

### Post by igorzwx on 2009-07-21
The easiest way to get explanation, is, perhaps, to ask on OSS4 forum.
Or read posts there.

---

### Post by ivanko.rus on 2009-07-21
I will try to compile the latest alsa...

---

### Post by ivanko.rus on 2009-07-21
It's giving me the following:
```
configure: error: *** libasound has no external plugin SDK
alsa-plugins-1.0.20 configure failed
```

---

### Post by igorzwx on 2009-07-21
Ivanko!

I do not think that it is easy to find a specialist on ALSA here.
You may get a help with pulse here...

---

### Post by ivanko.rus on 2009-07-21
Yeah, it looks like that... Even tried booting into Kubuntu LiveCD, the problem persists. Ok, I will try to write to alsa to see if they can do sth with it.

---

### Post by igorzwx on 2009-07-21
Try Slax or Goblin

Slax LiveCD shoud work, I presume.

---

### Post by ivanko.rus on 2009-07-21
After a lot of googling I found that the problem is pretty common and has NO solution yet :( And the bug is in many bugtrackers (including ALSA's), so I can not do anything, only buying a separate audio card (which I am going to do in the next future :))

---

### Post by Whiffle on 2009-07-21
Yeah I haven't seen a solution for this yet either.  Although, turning up the "Front" control on alsamixer seems to help enough.  Its loud enough to if it were any louder, i think my neighbors would complain...

---

### Post by jpt266 on 2009-07-21
I have this too. I can not find a fix. Let us hope a fix is posted soon.

---

### Post by ikt on 2009-07-22
> **ivanko.rus said:**
> After a lot of googling I found that the problem is pretty common and has NO solution yet :( And the bug is in many bugtrackers (including ALSA's), so I can not do anything, only buying a separate audio card (which I am going to do in the next future :))

are you able to link to the bug trackers ?

Just to save me having to run around and re-lot of googling. :)

---

### Post by ivanko.rus on 2009-07-23
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/217789](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/217789)
[https://bugs.launchpad.net/alsa-driver/+bug/107232](https://bugs.launchpad.net/alsa-driver/+bug/107232)

Here you have some :) Maybe there are more, but I didn't find them in my History.
Regards!

---

### Post by yoda2nd on 2009-07-31
I had the same problem.  At the time I was using a 3 way splitter to output to my computer speakers, reviver and wireless head phones.  As soon as I unpluged the wireless head phones the problem seems to go away.  I tried a several combinations of the 3.  Any time the wireless head phones were pluged in the sound level droped.  If you have multiple devices pluged in you might want to try un-plugging them one at a time to see if one of them is causing what I would assume is an impedance issue.

---

