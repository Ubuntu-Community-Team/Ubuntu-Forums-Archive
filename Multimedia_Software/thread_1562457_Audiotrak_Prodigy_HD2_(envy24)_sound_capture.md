---
title: "Audiotrak Prodigy HD2 (envy24) sound capture"
date: 2010-08-27
forum: Multimedia Software
---

### Post by medb on 2010-08-27
I have the sound card [Audiotrak Prodigy HD2]("http://www.audiotrak.net/products/prodigyhd2/"), and sound output under Ubuntu 10.10 is working perfectly.

But sound capture is not working at all: I can manage input level volume in the gnome-volume-control, but not in the alsamixer: I receive the message: "This sound device does not have any capture controls." also alsamixer can't handle the sound output volume.

When I try to record via the "Sound Recorder" volume changed in the sound bar but slightly. Seems as sound level is to low, but in the gnome-volume-manager it is set to the max value.

Also maybe the alsa driver not loaded, because when I try to run the envy24control and receive the next message: "No ICE1712 cards found", but as I mentioned above: the sound output is working perfectly.

There are no other sound cards in the system (on-board - disabled via BIOS and ATI HDMI audio disabled by adding corresponding kernel module to the blacklist).

Microphone is working well - tested under Windows.

Any suggestions to fix this?

P.S. Sorry for my English

---

### Post by cchhrriiss121212 on 2010-08-28
Could you post the results of aplay -l, arecord -l, and lspci -v?
Your English is perfect by the way.

---

### Post by medb on 2010-08-28
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICE1724 [ICEnsemble ICE1724], device 0: ICE1724 [ICE1724]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICE1724 [ICEnsemble ICE1724], device 1: ICE1724 IEC958 [ICE1724 IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: ICE1724 [ICEnsemble ICE1724], device 0: ICE1724 [ICE1724]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICE1724 [ICEnsemble ICE1724], device 1: ICE1724 IEC958 [ICE1724 IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ lspci -v
00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device 8239
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 8239
	Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 8239
	Flags: 66MHz, fast devsel, IRQ 255
	I/O ports at ff00 [size=64]
	I/O ports at 1c00 [size=64]
	I/O ports at 1c40 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. Device 8239
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Device 8239
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:04.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. Device 8239
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	I/O ports at fc00 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_amd
	Kernel modules: pata_amd

00:05.0 RAID bus controller: nVidia Corporation MCP55 SATA Controller (rev a2) (prog-if 85)
	Subsystem: ASUSTeK Computer Inc. Device 8239
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at f700 [size=16]
	Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: sata_nv
	Kernel modules: sata_nv

00:05.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Device 8239
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	I/O ports at 09e0 [size=8]
	I/O ports at 0be0 [size=4]
	I/O ports at 0960 [size=8]
	I/O ports at 0b60 [size=4]
	I/O ports at f200 [size=16]
	Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: sata_nv
	Kernel modules: sata_nv

00:05.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Device 8239
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	I/O ports at f100 [size=8]
	I/O ports at f000 [size=4]
	I/O ports at ef00 [size=8]
	I/O ports at ee00 [size=4]
	I/O ports at ed00 [size=16]
	Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: sata_nv
	Kernel modules: sata_nv

00:06.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000d000-0000dfff
	Capabilities: <access denied>

00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 8239
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 41
	Memory at fe02a000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at ec00 [size=8]
	Memory at fe029000 (32-bit, non-prefetchable) [size=256]
	Memory at fe028000 (32-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fde00000-fdefffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
	Flags: fast devsel
	Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>
	Kernel driver in use: k10temp
	Kernel modules: k10temp

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
	Flags: fast devsel

01:08.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
	Subsystem: VIA Technologies Inc. Device 2401
	Flags: bus master, medium devsel, latency 32, IRQ 18
	I/O ports at dc00 [size=32]
	I/O ports at d800 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: ICE1724
	Kernel modules: snd-ice1724

02:00.0 VGA compatible controller: ATI Technologies Inc RV770 [Radeon HD 4850] (prog-if 00 [VGA controller])
	Subsystem: ATI Technologies Inc Device 0502
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at fdee0000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at cc00 [size=256]
	Expansion ROM at fdec0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel modules: radeon

02:00.1 Audio device: ATI Technologies Inc HD48x0 audio
	Subsystem: ATI Technologies Inc HD48x0 audio
	Flags: bus master, fast devsel, latency 0, IRQ 5
	Memory at fdefc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel

Hope this helps :)

---

### Post by cchhrriiss121212 on 2010-08-28
That all looks fine to me, the card is recognised and the system has the ice1724 module loaded, which means the following is just a guess. 
You could try adding yourself to the audio group and then reinstalling envy24, and if that fails try upgrading ALSA.

---

### Post by medb on 2010-08-29
Unfortunately, I already have installed the latest alsa (1.0.23) and my user is already in the "audio" group.
Also, reinstalling the alsa didn't help.

Below I have posted screenshots of the various volume-control tools, maybe this will help.

alsamixer:
[ATTACH]167813[/ATTACH]

GNOME ALSA Mixer:
[ATTACH]167814[/ATTACH]

gnome-volume-control:
[ATTACH]167815[/ATTACH]

PulseAudio Volume Control:
[ATTACH]167816[/ATTACH]

Sound Recorder:
[ATTACH]167817[/ATTACH]

On the last screenshot at the bottom of the window placed progress bar "Level", which indicates the highest volume level that I can achieve during recording.
The volume level is changed when I speak into the microphone, but very slightly. And there is no voice while playing the record, only noise.

---

### Post by medb on 2010-09-09
Sorry, guys. But actually the microphone was broken (it was wrongly tested with a laptop). It seemed that it was working, because the built-in microphone continuing capture sound even when the external microphone was plugged-in.

After replacing of the microphone all is working fine, thanks.

---

