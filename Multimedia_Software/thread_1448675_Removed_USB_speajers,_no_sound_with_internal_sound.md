---
title: "Removed USB speajers, no sound with internal sound card"
date: 2010-04-06
forum: Multimedia Software
---

### Post by LinuxBob on 2010-04-06
I took out some USB speakers that had been working for many months because I needed them on another PC. I plugged the audio out (lime colored female connector on back of Ubuntu PC) into my stereo receiver's VCR audio in (Red and white jacks), no sound. Yes, the cable is fine (same cable I took off the other PC which was working fine), and the receiver is set to VCR.


I recall having to go through some hoops to get the USB speakers working way back when. The Pulseaudio volume control shows left and right pulsating bars when I have on Pandora, but sound is obviously not being sent to the right output. I also tried the optical audio out on the PC into the receiver's DBS optical in but again no sound.

Any ideas?

When I set up the USB speakers I believe I had to change the line in /etc/modprobe.d/alsa-base.conf


options snd-hda-intel probe_mask=8 model=3stack

I had to overwrite whatever was there model=xxxx with "3stack"


What was there? I have HDA nVidia sound card MCP79 and IEC958 shows up in alsamixer but no volume bars for anything at all, just blank alsamixer with sound card info.

Also, once I update /etc/modprobe.d/alsa-base.conf I then have to shut down or restart alsa and/or pulseaudio, anyone know the sequence of commands?

Some terminal  output:


$aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

zareason:/etc/modprobe.d$ lspci -v
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
	Subsystem: nVidia Corporation Device cb79
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
	Subsystem: nVidia Corporation Device cb79
	Flags: bus master, 66MHz, fast devsel, latency 0

00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
	Subsystem: ZOTAC International (MCO) Ltd. Device a108
	Flags: bus master, 66MHz, fast devsel, latency 0
	I/O ports at 4f00 [size=256]

00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
	Subsystem: ZOTAC International (MCO) Ltd. Device a108
	Flags: 66MHz, fast devsel

00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
	Subsystem: ZOTAC International (MCO) Ltd. Device a108
	Flags: 66MHz, fast devsel, IRQ 11
	I/O ports at 4900 [size=64]
	I/O ports at 4d00 [size=64]
	I/O ports at 4e00 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
	Subsystem: nVidia Corporation Device cb79
	Flags: 66MHz, fast devsel

00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
	Subsystem: ZOTAC International (MCO) Ltd. Device a108
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 9
	Memory at fae80000 (32-bit, non-prefetchable) [size=512K]

00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1) (prog-if 10)
	Subsystem: ZOTAC International (MCO) Ltd. Device a108
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at fae7f000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1) (prog-if 20)
	Subsystem: ZOTAC International (MCO) Ltd. Device a108
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at fae7ec00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1) (prog-if 10)
	Subsystem: ZOTAC International (MCO) Ltd. Device a108
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at fae7d000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1) (prog-if 20)
	Subsystem: ZOTAC International (MCO) Ltd. Device a108
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at fae7e800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
	Subsystem: PC Partner Limited Device 437b
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at fae78000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1) (prog-if 01)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	Capabilities: <access denied>

00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
	Subsystem: ZOTAC International (MCO) Ltd. Device a108
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at fae7c000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at d080 [size=8]
	Memory at fae7e400 (32-bit, non-prefetchable) [size=256]
	Memory at fae7e000 (32-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:0b.0 SATA controller: nVidia Corporation MCP79 AHCI Controller (rev b1) (prog-if 01)
	Subsystem: ZOTAC International (MCO) Ltd. Device a108
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 29
	I/O ports at d000 [size=8]
	I/O ports at cc00 [size=4]
	I/O ports at c880 [size=8]
	I/O ports at c800 [size=4]
	I/O ports at c480 [size=16]
	Memory at fae76000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: faf00000-fbffffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000f9ffffff
	Capabilities: <access denied>
	Kernel modules: shpchp

00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:18.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

03:00.0 VGA compatible controller: nVidia Corporation ION VGA (rev b1)
	Subsystem: ZOTAC International (MCO) Ltd. Device a108
	Flags: bus master, fast devsel, latency 0, IRQ 20
	Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at f8000000 (64-bit, prefetchable) [size=32M]
	I/O ports at ec00 [size=128]
	[virtual] Expansion ROM at fafe0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

---

