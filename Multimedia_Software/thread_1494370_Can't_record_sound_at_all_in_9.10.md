---
title: "Can't record sound at all in 9.10"
date: 2010-05-26
forum: Multimedia Software
---

### Post by pmooney78 on 2010-05-26
I just upgraded from 8.10 to 9.04, then rapidly to 9.10, when support for 8.10 was finally phased out. I've been trying for a few days to figure out how to record sound and can't get anything working. Sound playback works fine.

Here's what I've tried so far: 

```

arecord -d 10 -f cd -t wav -D front foobar.wav
rec -c1 hoopyfrood.aiff trim 0 10

```

from a terminal, and using the GUI in Audacity.

The terminal programs execute and quit after ten seconds, as expected, and create a sound of the appropriate length in my home directory, which is what I want. They don't report any errors, but the sound file they create is just soft background static with occasional soft clicks. Audacity also just records soft static with soft occasional clicks. The Gnome Sound recorder does slightly better, recording almost-intelligible sounds with bad static distortion.

I've verified that sound levels are not muted using the mixer, and have run through the Comprehensive Sound Problem Solutions Guide [[http://ubuntuforums.org/showthread.php?t=205449]](http://ubuntuforums.org/showthread.php?t=205449]). No joy. 

Here's the output of lscpi -v:

```

0:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
	Subsystem: Hewlett-Packard Company Device 30cc
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: cc000000-ceffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
	Subsystem: Hewlett-Packard Company Device 30cc
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1800 [size=32]
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
	Subsystem: Hewlett-Packard Company Device 30cc
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1820 [size=32]
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 30cc
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at f8404800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 30cc
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f8400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	I/O behind bridge: 00004000-00007fff
	Memory behind bridge: f4000000-f5ffffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f1ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=07, sec-latency=0
	I/O behind bridge: 00008000-0000bfff
	Memory behind bridge: f6000000-f7ffffff
	Prefetchable memory behind bridge: 00000000f2000000-00000000f3ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: f8000000-f80fffff
	Prefetchable memory behind bridge: 0000000080000000-00000000800fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
	Subsystem: Hewlett-Packard Company Device 30cc
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1840 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
	Subsystem: Hewlett-Packard Company Device 30cc
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1860 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
	Subsystem: Hewlett-Packard Company Device 30cc
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1880 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 30cc
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f8404c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=32
	Memory behind bridge: f8100000-f81fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 30cc
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Hewlett-Packard Company Device 30cc
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 18a0 [size=16]
	Kernel driver in use: ata_piix

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01)
	Subsystem: Hewlett-Packard Company Device 30cc
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 28
	I/O ports at 18d8 [size=8]
	I/O ports at 18cc [size=4]
	I/O ports at 18d0 [size=8]
	I/O ports at 18c8 [size=4]
	I/O ports at 18e0 [size=32]
	Memory at f8404000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 30cc
	Flags: medium devsel, IRQ 10
	Memory at 80100000 (32-bit, non-prefetchable) [size=256]
	I/O ports at 1c00 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400M GS] (rev a1)
	Subsystem: Hewlett-Packard Company Device 30cc
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at ce000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at cc000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 2000 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
	Subsystem: Hewlett-Packard Company Device 135b
	Flags: bus master, fast devsel, latency 0, IRQ 30
	Memory at f4000000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: iwl3945
	Kernel modules: iwl3945

08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
	Subsystem: Hewlett-Packard Company Device 30cc
	Flags: bus master, fast devsel, latency 0, IRQ 29
	I/O ports at c000 [size=256]
	Memory at f8000000 (64-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at 80000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

09:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 30cc
	Flags: bus master, medium devsel, latency 32, IRQ 20
	Memory at f8100000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

09:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
	Subsystem: Hewlett-Packard Company Device 30cc
	Flags: bus master, medium devsel, latency 32, IRQ 21
	Memory at f8100800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

09:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
	Subsystem: Hewlett-Packard Company Device 30cc
	Flags: bus master, medium devsel, latency 32, IRQ 11
	Memory at f8100c00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ricoh-mmc
	Kernel modules: ricoh_mmc

09:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
	Subsystem: Hewlett-Packard Company Device 30cc
	Flags: bus master, medium devsel, latency 32, IRQ 11
	Memory at f8101000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

09:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff) (prog-if ff)
	!!! Unknown header type 7f

```

I'm running Ubuntu 9.10 on an HP Pavilion dv6000 with a Centrino Duo processor and 2GB of RAM. Any suggestions appreciated.

---

### Post by pmooney78 on 2010-05-28
Bump.

---

### Post by lidex on 2010-05-30
First, for mic problem, check this.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

Then use pulseaudio volume control (pavucontrol) to select your mic in 'Input Devices' tab.

From alsa documentation:
> Capture Problems
~~~~~~~~~~~~~~~~
The capture problems are often because of missing setups of mixers.
Thus, before submitting a bug report, make sure that you set up the
mixer correctly.  For example, both "Capture Volume" and "Capture
Switch" have to be set properly in addition to the right "Capture
Source" or "Input Source" selection.  Some devices have "Mic Boost"
volume or switch.

When the PCM device is opened via "default" PCM (without pulse-audio
plugin), you'll likely have "Digital Capture Volume" control as well.
This is provided for the extra gain/attenuation of the signal in
software, especially for the inputs without the hardware volume
control such as digital microphones.  Unless really needed, this
should be set to exactly 50%, corresponding to 0dB -- neither extra
gain nor attenuation.  When you use "hw" PCM, i.e., a raw access PCM,
this control will have no influence, though.

---

### Post by pmooney78 on 2010-05-30
Thank you!

I played around with leveling options in both mixers until I found a combination that works.

Whew. How annoying. There MUST be an easier way to handle that.

---

### Post by lidex on 2010-05-31
> **pmooney78 said:**
> Thank you!

I played around with leveling options in both mixers until I found a combination that works.

Whew. How annoying. There MUST be an easier way to handle that.
Tell me!
10 users can have the same problem and all have a different solution. :confused: Glad your's is fixed though. Please mark the thread as solved using 'Thread Tools' up top.

---

### Post by map445 on 2010-06-06
> **lidex said:**
> First, for mic problem, check this.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

Then use pulseaudio volume control (pavucontrol) to select your mic in 'Input Devices' tab.

From alsa documentation:

Thank You Lidex.
I am using 10.04 LTS but, there was no alsamixer.  When I tried to record, I could hear very slight sound.  Now, I can hear the sound since installing alsamixer.:)

---

