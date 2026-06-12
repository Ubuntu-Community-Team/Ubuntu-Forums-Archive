---
title: "Problems with sound"
date: 2008-09-06
forum: Multimedia Software
---

### Post by Sicarul on 2008-09-06
Hello, i have two problems, i have been looking for solutions here and in google but couldn't find anything related to these particular problems, so i will describe them here.

Please note that they aren't serious problems, but they are really annoying in a day-to-day basis, so if anyone already knows a solution or can give me a few pointers i will be thankful.

**[SIZE="5"]My computer information[/SIZE]**
Information you might find useful

My computer is an "Olivetti 520", it's a Laptop with the following features:
- Pentium Dual Core 1.4 Ghz
- 1GB Ram
- 120GB Hard Drive
- SiS Mirage 3 Video
- Realtek RTL8187 Wi-Fi
- Multi-Card Reader 5 in 1
- 4 USB ports
- VGA output

**Edit: In order to boot, i have to use the following parameters, otherwise, it doesn't boot:**
```
pci=assign-busses apic miantimer idle=poll reboot=cold,hard
```

```
sicarul@sicarul-olibook:~$ sudo lspci -v
[sudo] password for sicarul: 
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
	Subsystem: Elitegroup Computer Systems Unknown device 5050
	Flags: bus master, medium devsel, latency 32
	Memory at a0000000 (32-bit, non-prefetchable) [size=256M]
	Capabilities: [c0] AGP version 3.5

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: b0000000-b00fffff
	Prefetchable memory behind bridge: c0000000-cfffffff

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
	Subsystem: Elitegroup Computer Systems Unknown device 5a00
	Flags: bus master, medium devsel, latency 0

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01) (prog-if 80 [Master])
	Subsystem: Elitegroup Computer Systems Unknown device 5a00
	Flags: bus master, medium devsel, latency 128, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1080 [size=16]
	Capabilities: [58] Power Management version 2

00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10 [OHCI])
	Subsystem: Elitegroup Computer Systems Unknown device 5a00
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at b0104000 (32-bit, non-prefetchable) [size=4K]

00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10 [OHCI])
	Subsystem: Elitegroup Computer Systems Unknown device 5a00
	Flags: bus master, medium devsel, latency 32, IRQ 19
	Memory at b0105000 (32-bit, non-prefetchable) [size=4K]

00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20 [EHCI])
	Subsystem: Elitegroup Computer Systems Unknown device 5a00
	Flags: bus master, medium devsel, latency 32, IRQ 20
	Memory at b0106000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [50] Power Management version 2

00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
	Subsystem: Elitegroup Computer Systems Unknown device 5a00
	Flags: bus master, medium devsel, latency 0, IRQ 21
	Memory at b0307000 (32-bit, non-prefetchable) [size=128]
	I/O ports at 1000 [size=128]
	Capabilities: [40] Power Management version 2

00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Silicon Integrated Systems [SiS] SATA Controller / IDE mode
	Flags: bus master, medium devsel, latency 32, IRQ 17
	I/O ports at 10c8 [size=8]
	I/O ports at 10bc [size=4]
	I/O ports at 10c0 [size=8]
	I/O ports at 10b8 [size=4]
	I/O ports at 10a0 [size=16]
	Capabilities: [58] Power Management version 2

00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
	Subsystem: Elitegroup Computer Systems Unknown device 5a00
	Flags: bus master, medium devsel, latency 0, IRQ 22
	Memory at b0100000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10) (prog-if 00 [VGA controller])
	Subsystem: Elitegroup Computer Systems Unknown device 5050
	Flags: 66MHz, medium devsel, IRQ 9
	BIST result: 00
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at b0000000 (32-bit, non-prefetchable) [size=128K]
	I/O ports at 9000 [size=128]
	Capabilities: [40] Power Management version 2
	Capabilities: [50] AGP version 3.0

```

```
sicarul@sicarul-olibook:~$ cat /proc/asound/cards
 0 [SIS966         ]: HDA-Intel - HDA SIS966
                      HDA SIS966 at 0xb0100000 irq 22

```

```
sicarul@sicarul-olibook:~$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [off]
  Front Right: Playback 31 [100%] [12.00dB] [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [33.00dB] [on]
  Front Right: Capture 31 [100%] [33.00dB] [on]
Simple mixer control 'Caller ID',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Digital',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 60 [50%] [0.00dB]
  Front Right: Capture 60 [50%] [0.00dB]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Front Mic'
  Item0: 'Front Mic'
Simple mixer control 'Off-hook',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]

```

**(BOTH PROBLEMS SOLVED)**

[SIZE="5"]Problem 1[/SIZE]
*Ok, here's my main problem:*
Each time i boot my computer, it doesn't detect i have my speakers plugged in, so i have to unplug and plug them, otherwise, it uses the integrated speakers the laptop has (Craaaaapy).
It detects them when i do that for some reason, but doesn't if they were already plugged when i booted the machine.

[SIZE="5"]Problem 2[/SIZE]
*Here's a minor problem, but still a problem:*
I can't record with the integrated microphone the laptop has, i can only record if i plug a microphone in.
The strange thing is if i enable playing the input of "Front mic" i can hear whichever i say(or hit) so it IS working, but i can't capture with any program(Tried with many programs, all capture only if it is an external microphone).
I have already set Front mic as the input source, and it didn't work.

**Goodbye, thanks for reading ^_^, *any* input is appreciated**

**EDIT:**
Sorry for not searching enough, i could solve both problems in one shot by using the option lenovo-101e on the snd-hda-intel module, as described in [http://ubuntuforums.org/showthread.php?t=616845]("http://ubuntuforums.org/showthread.php?t=616845") sorry for the topic and i hope it helps anybody with this or a similar computer. Thanks for such an excelent resource as this forums!

Bye again!

---

