---
title: "enabling pulseaudio equalizer garbles sound"
date: 2010-01-26
forum: Multimedia Software
---

### Post by arinekhen on 2010-01-26
I installed the pulseaudio equalizer today on my Karmic desktop using the instructions at [http://ubuntuforums.org/showthread.php?t=1308838](http://ubuntuforums.org/showthread.php?t=1308838)

When I enable the equalizer via the GUI checkbox, my sound instantly becomes garbled. When I disable it the problem disappears, but then I can't use the equalizer, which was the point of the exercise. :-)

I found some suggestions about editing /etc/pulse/default.pa, but the parameters concerning module-hal-* don't appear in my default.pa. I also have read through a couple of Audio Troubleshooting guides without finding this particular symptom. 

I have exhausted my google-fu, and I would really appreciate some help if possible.

Here's what little diagnostic info I can offer:

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci -v
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
	Subsystem: Dell Device 027f
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fe900000-feafffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:03.0 Communication controller: Intel Corporation 4 Series Chipset HECI Controller (rev 03)
	Subsystem: Dell Device 027f
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at feda6000 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: heci
	Kernel modules: heci

00:03.2 IDE interface: Intel Corporation 4 Series Chipset PT IDER Controller (rev 03) (prog-if 85 [Master SecO PriO])
	Subsystem: Dell Device 027f
	Flags: 66MHz, fast devsel, IRQ 18
	I/O ports at fe80 [size=8]
	I/O ports at fe90 [size=4]
	I/O ports at fea0 [size=8]
	I/O ports at feb0 [size=4]
	I/O ports at fef0 [size=16]
	Capabilities: <access denied>

00:03.3 Serial controller: Intel Corporation 4 Series Chipset Serial KT Controller (rev 03) (prog-if 02)
	Subsystem: Dell Device 027f
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
	I/O ports at ec98 [size=8]
	Memory at febd8000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: serial

00:19.0 Ethernet controller: Intel Corporation 82567LM-3 Gigabit Network Connection (rev 02)
	Subsystem: Dell Device 027f
	Flags: bus master, fast devsel, latency 0, IRQ 33
	Memory at febe0000 (32-bit, non-prefetchable) [size=128K]
	Memory at febd9000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at ecc0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: e1000e
	Kernel modules: e1000e

00:1a.0 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #4 (rev 02)
	Subsystem: Dell Device 027f
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at ff20 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #5 (rev 02)
	Subsystem: Dell Device 027f
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at ff00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.2 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #6 (rev 02)
	Subsystem: Dell Device 027f
	Flags: bus master, medium devsel, latency 0, IRQ 22
	I/O ports at fc00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20)
	Subsystem: Dell Device 027f
	Flags: bus master, medium devsel, latency 0, IRQ 22
	Memory at febda000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801JD/DO (ICH10 Family) HD Audio Controller (rev 02)
	Subsystem: Dell Device 027f
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at febdc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801JD/DO (ICH10 Family) PCI Express Port 1 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Memory behind bridge: fe800000-fe8fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801JD/DO (ICH10 Family) PCI Express Port 2 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: fe700000-fe7fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #1 (rev 02)
	Subsystem: Dell Device 027f
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at ff80 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #2 (rev 02)
	Subsystem: Dell Device 027f
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at ff60 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #3 (rev 02)
	Subsystem: Dell Device 027f
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at ff40 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20)
	Subsystem: Dell Device 027f
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at ff980000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a2) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801JD (ICH10D) LPC Interface Controller (rev 02)
	Subsystem: Dell Device 027f
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02) (prog-if 01)
	Subsystem: Dell Device 027f
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 32
	I/O ports at fe00 [size=8]
	I/O ports at fe10 [size=4]
	I/O ports at fe20 [size=8]
	I/O ports at fe30 [size=4]
	I/O ports at fec0 [size=32]
	Memory at ff970000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801JD/DO (ICH10 Family) SMBus Controller (rev 02)
	Subsystem: Dell Device 027f
	Flags: medium devsel, IRQ 9
	Memory at febdb000 (64-bit, non-prefetchable) [size=256]
	I/O ports at ece0 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3450
	Subsystem: Dell Device 0342
	Flags: bus master, fast devsel, latency 0, IRQ 34
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fe9f0000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at dc00 [size=256]
	Expansion ROM at fea00000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx, radeon

---

### Post by joel007 on 2010-04-12
I'm facing exactly the same problem. U can try this:

add LADSPA output:
	paste qpaeq.py into /usr/bin	(improves the quality a little bit, but uses too much of processor)
 receive updates for pulseaudio-equalizer:
	run in terminal: sudo add-apt-repository ppa:psyke83/ppa

The sound quality should get stabilized, however, scrolling the volume up&down will still result jerky. I'm gonna carry on trying, if I find something, I'll let u know...

---

### Post by almightybunghole on 2011-03-29
Hi Joel, did you ever manage to sort out the jerky sound when using the volume slider? I've just installed the pulseaudio equalizer from webupd8's PPA but I'm getting the same problem. Any ideas?

---

### Post by joel007 on 2011-03-29
unfortunatelly not :confused: but i have got quite used to it. as u might have realized, the PPA I mentioned above doesn't work any more, by the way (in U10.10), so u have to manually download the "pulseaudio-equalizer_2.7.0.1-1_all.deb" version.  previous versions don't work any more in U10.10. also pulesaudio sucks a lot, so I had to switch to vlc. I'd say everything has only got worse :( otherwise I welcome any interesting hints on this program.

---

