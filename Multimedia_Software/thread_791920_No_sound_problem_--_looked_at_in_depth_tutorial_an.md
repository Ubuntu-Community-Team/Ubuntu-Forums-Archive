---
title: "No sound problem -- looked at in depth tutorial and linux does detect my soundcard"
date: 2008-05-12
forum: Multimedia Software
---

### Post by P373 on 2008-05-12
Hello; I've installed linux 8 and the sound doesn't work even though linux detects my sound card. here is the stuff from the terminal, although I don't know what to do with it.

Any suggestion on making sound come out? Thanks.

```
davidmacdonald@davidmacdonald-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audigy2 [Audigy 2 ZS [SB0353]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 1: Audigy2 [Audigy 2 ZS [SB0353]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Audigy2 [Audigy 2 ZS [SB0353]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audigy2 [Audigy 2 ZS [SB0353]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
davidmacdonald@davidmacdonald-desktop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
	Subsystem: Dell Unknown device 0174
	Flags: bus master, fast devsel, latency 0
	Memory at d8000000 (32-bit, prefetchable) [size=128M]
	Capabilities: <access denied>

00:02.0 Display controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
	Subsystem: Dell Unknown device 0174
	Flags: fast devsel, IRQ 11
	Memory at d0000000 (32-bit, prefetchable) [disabled] [size=128M]
	Memory at feb80000 (32-bit, non-prefetchable) [disabled] [size=512K]
	I/O ports at ed98 [disabled] [size=8]
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 0174
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at ff80 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 0174
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at ff60 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 0174
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at ff40 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 0174
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at ff20 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
	Subsystem: Dell Unknown device 0174
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fb000000-feafffff
	Prefetchable memory behind bridge: e0000000-efffffff

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
	Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Dell Unknown device 0174
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ffa0 [size=16]
	Memory at feb7fc00 (32-bit, non-prefetchable) [size=1K]

00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Dell Unknown device 0174
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
	I/O ports at fe00 [size=8]
	I/O ports at fe10 [size=4]
	I/O ports at fe20 [size=8]
	I/O ports at fe30 [size=4]
	I/O ports at fea0 [size=16]

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
	Subsystem: Dell Unknown device 0174
	Flags: medium devsel, IRQ 3
	I/O ports at eda0 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
	Subsystem: Dell Unknown device 0174
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at ee00 [size=256]
	I/O ports at edc0 [size=64]
	Memory at feb7fa00 (32-bit, non-prefetchable) [size=512]
	Memory at feb7f900 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1) (prog-if 00 [VGA controller])
	Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 23
	Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (32-bit, prefetchable) [size=256M]
	Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at fe000000 [disabled] [size=128K]
	Capabilities: <access denied>

01:01.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
	Subsystem: ATI Technologies Inc Unknown device 00f9
	Flags: bus master, medium devsel, latency 64, IRQ 22
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: <access denied>

01:02.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
	Subsystem: Creative Labs Unknown device 1003
	Flags: bus master, medium devsel, latency 64, IRQ 21
	I/O ports at df00 [size=64]
	Capabilities: <access denied>

01:02.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04) (prog-if 10 [OHCI])
	Subsystem: Creative Labs SB Audigy FireWire Port
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at fe9fa800 (32-bit, non-prefetchable) [size=2K]
	Memory at fe9fc000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
	Subsystem: Dell Unknown device 0174
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at fe9fb000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at df40 [size=64]
	Capabilities: <access denied>

davidmacdonald@davidmacdonald-desktop:~$ 
davidmacdonald@davidmacdonald-desktop:~$ sudo modprobe snd-
Display all 159 possibilities? (y or n)
snd-ac97-codec      snd-es1938          snd-pcm-oss
snd-ad1816a         snd-es1968          snd-pcsp
snd-ad1848          snd-es968           snd-pcxhr
snd-ad1848-lib      snd-fm801           snd-pdaudiocf
snd-ad1889          snd-gina20          snd-pdplus
snd-adlib           snd-gina24          snd-portman2x4
snd-ak4114          snd-gusclassic      snd-pt2258
snd-ak4117          snd-gusextreme      snd-rawmidi
snd-ak4531-codec    snd-gus-lib         snd-riptide
snd-ak4xxx-adda     snd-gusmax          snd-rme32
snd-ali5451         snd-hda-intel       snd-rme96
snd-aloop           snd-hdsp            snd-rme9652
snd-als100          snd-hdspm           snd-rtctimer
snd-als300          snd-hifier          snd-sb16
snd-als4000         snd-hwdep           snd-sb16-csp
snd-asihpi          snd-i2c             snd-sb16-dsp
snd-atiixp          snd-ice1712         snd-sb8
snd-atiixp-modem    snd-ice1724         snd-sb8-dsp
snd-au8810          snd-ice17xx-ak4xxx  snd-sbawe
snd-au8820          snd-indigo          snd-sb-common
snd-au8830          snd-indigodj        snd-sc6000
snd-azt2320         snd-indigoio        snd-seq
snd-azt3328         snd-intel8x0        snd-seq-device
--More--

```

---

