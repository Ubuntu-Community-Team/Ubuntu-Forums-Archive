---
title: "EMU10k1x not found - Lucid"
date: 2010-10-30
forum: Multimedia Software
---

### Post by AMindUnited on 2010-10-30
I recently installed a new sound card in one of my computers but it's not showing up in pulse. It's also not showing up in ALSA. It is, however, showing up when I lspci as: Creative Labs [SB Live! Value] EMU10k1x.
I've tried doing a fresh install, I've tried other varients, I've disabled the onBoard soundcard in the BIOS to prevent any conflicts, but have little idea what else to do.
Anyone have a suggestions?

---

### Post by cchhrriiss121212 on 2010-10-30
Can you post lspci -v and aplay -l outputs?

What is the name of the card? Brand + model

---

### Post by AMindUnited on 2010-10-30
Hey cchhrriiss121212 thanks for the reply!
the card is a "Ritmo" model CC-T850

0:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
	Subsystem: Giga-byte Technology Device 5001
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
	Subsystem: Giga-byte Technology Device 0c11
	Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
	Subsystem: Giga-byte Technology Device 0c11
	Flags: 66MHz, fast devsel, IRQ 10
	I/O ports at c400 [size=64]
	I/O ports at 1c00 [size=64]
	I/O ports at c000 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
	Subsystem: Giga-byte Technology Device 0c11
	Flags: 66MHz, fast devsel

00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3) (prog-if 10)
	Subsystem: Giga-byte Technology Device 5004
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at fb007000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3) (prog-if 20)
	Subsystem: Giga-byte Technology Device 5004
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at fb006000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1) (prog-if 01)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000a000-0000afff
	Capabilities: <access denied>

00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
	Subsystem: Giga-byte Technology Device a002
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at fb000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2) (prog-if 8a [Master SecP PriP])
	Subsystem: Giga-byte Technology Device 5002
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at f000 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_amd
	Kernel modules: pata_amd

00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
	Subsystem: Giga-byte Technology Device e000
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 25
	Memory at fb004000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at c800 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: Giga-byte Technology Device b002
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at dc00 [size=16]
	Memory at fb005000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: sata_nv
	Kernel modules: sata_nv

00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: f8000000-faffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000efffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel
	Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:07.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X
	Subsystem: Creative Labs Device 1003
	Flags: bus master, medium devsel, latency 32, IRQ 11
	I/O ports at a000 [size=32]
	Capabilities: <access denied>
	Kernel modules: snd-emu10k1x

01:07.1 Input device controller: Creative Labs [SB Live! Value] Input device controller
	Subsystem: Creative Labs Device 1003
	Flags: bus master, medium devsel, latency 32
	I/O ports at a400 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: Emu10k1_gameport
	Kernel modules: emu10k1-gp

02:00.0 VGA compatible controller: nVidia Corporation GT216 [GeForce GT 220] (rev a2)
	Subsystem: Micro-Star International Co., Ltd. Device 8051
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f8000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at e0000000 (64-bit, prefetchable) [size=32M]
	I/O ports at b000 [size=128]
	[virtual] Expansion ROM at e2000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidiafb, nouveau

02:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
	Subsystem: Micro-Star International Co., Ltd. Device 8051
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fa000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

randr@MediaCenter:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

...Right just realised, I've re-enabled the onboard sound in the BIOS (I was just watching a movie)

---

### Post by cchhrriiss121212 on 2010-10-30
> 01:07.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X
	Subsystem: Creative Labs Device 1003
	Flags: bus master, medium devsel, latency 32, IRQ 11
	I/O ports at a000 [size=32]
	Capabilities: <access denied>
	Kernel modules: snd-emu10k1x
So this appears to be your card, but as this card is not officially supported it has been recognised as a Creative Labs card. I can't say whether this card will actually work or not, but if it uses the same chipset as the Creative then it could be fine. In the future, try to research supported hardware before buying, as support for Linux is patchy at best.

Try this:
sudo modprobe snd-emu10k1x

Then try aplay -l again.

---

### Post by AMindUnited on 2010-10-30
modprobe went badly:
randr@MediaCenter:~$ sudo modprobe snd-emu10k1x
[sudo] password for randr: 
WARNING: /etc/modprobe.d/alsa-base.conf line 29: ignoring bad line starting with '$CMDLINE_OPTS'
WARNING: /etc/modprobe.d/alsa-base.conf line 29: ignoring bad line starting with '$CMDLINE_OPTS'
FATAL: Module snd_emk10k1x not found.
FATAL: Error running install command for snd_emu10k1x

---

### Post by cchhrriiss121212 on 2010-10-30
What do you get if you type:
sudo modprobe snd-
then press tab?

---

### Post by AMindUnited on 2010-10-30
ya, it does get listed.

---

### Post by AMindUnited on 2010-10-30
Wait i know the cause of that error:
FATAL: Module snd_emk10k1x not found. (left over for something I tried 10hrs ago)

I fixed that up and then:
randr@MediaCenter:~$ sudo modprobe snd-emu10k1x
randr@MediaCenter:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by cchhrriiss121212 on 2010-10-30
I've been googling this brand for a while now, but I can't seem to find any documented linux users out there, so I would say that this is a dead end. Sorry.

---

### Post by AMindUnited on 2010-10-30
Well it was $10 card, no worries.
Thanks so much for the help.

---

