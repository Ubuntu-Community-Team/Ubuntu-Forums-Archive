---
title: "half working soundcard after perfect liveCd"
date: 2011-03-17
forum: Multimedia Software
---

### Post by mathieujohnson on 2011-03-17
Hi,

I just installed 10.10, I've been using linux for the past 6 years and this is the first time i see this happen.

When loading the live cd my soundcard works perfectly, its there in lspci, the proper module gets loaded and when I check in sound preferences through the speaker icon, my soundcard is in the hardware tab. Proper input and outputs are in the input and output tabs also. Audio playback is normal.

After install, though, my soundcard is still in lspci and the module also gets loaded but in sound preferences, there is absolutely nothing in the hardware tab, even though inputs and outputs are visible in the input and output tabs. The playback is NOT normal. It stutters and skips and seems to be lagging.

Now, I have tried a new kernel, an older kernel, purge-ing the sound related packages (per the sticky on this forum) and re-installing them without any changes at all!

Does anyone know why this is happening?
p.s. I also tried linux mint 9 and the same thing happened!

lspci -v
```

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 81c0
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 81c0
	Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 81c0
	Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 81c0
	Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 81c0
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 81c0
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 81c0
	Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 81c0
	Flags: 66MHz, fast devsel

00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: fa000000-fcffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 81c0
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 81c0
	Flags: bus master, 66MHz, fast devsel, latency 0

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 81c0
	Flags: 66MHz, fast devsel, IRQ 255
	I/O ports at 4c00 [size=64]
	I/O ports at 4c40 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 81c0
	Flags: 66MHz, fast devsel

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. Device 81c0
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Device 81c0
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. Device 81c0
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	I/O ports at f400 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_amd
	Kernel modules: pata_amd

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Device 81c0
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at e000 [size=16]
	Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: sata_nv
	Kernel modules: sata_nv

00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Device 81c0
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	I/O ports at 09e0 [size=8]
	I/O ports at 0be0 [size=4]
	I/O ports at 0960 [size=8]
	I/O ports at 0b60 [size=4]
	I/O ports at cc00 [size=16]
	Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: sata_nv
	Kernel modules: sata_nv

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=128
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: fdd00000-fddfffff
	Prefetchable memory behind bridge: fde00000-fdefffff
	Capabilities: <access denied>

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device 816a
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at c800 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE/7200 GS] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Device 8250
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fb000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at fcfe0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nouveau, nvidiafb

02:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
	Flags: bus master, medium devsel, latency 32, IRQ 19
	Memory at fddff000 (32-bit, non-prefetchable) [size=2K]
	Memory at fddf8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci, ohci1394

02:09.0 Multimedia audio controller: Aureal Semiconductor Vortex 1 (rev 02)
	Subsystem: Diamond Multimedia Systems Sonic Impact A3D
	Flags: bus master, medium devsel, latency 32, IRQ 17
	Memory at fddc0000 (32-bit, non-prefetchable) [size=128K]
	I/O ports at bc00 [size=8]
	I/O ports at b800 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: au8820
	Kernel modules: snd-au8820

```


lsmod
```

Module                  Size  Used by
binfmt_misc             6599  1 
vboxnetadp              6454  0 
vboxnetflt             15152  0 
vboxdrv               190199  2 vboxnetadp,vboxnetflt
snd_au8820             26758  2 
snd_ac97_codec         99227  1 snd_au8820
nvidia               9329739  40 
snd_pcm                71475  2 snd_au8820,snd_ac97_codec
snd_page_alloc          7120  1 snd_pcm
ac97_bus                1014  1 snd_ac97_codec
snd_mpu401_uart         5661  1 snd_au8820
snd_seq_midi            4588  0 
snd_rawmidi            17783  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    49038  12 snd_au8820,snd_ac97_codec,snd_pcm,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore                880  1 snd
ns558                   3068  0 
i2c_nforce2             5179  0 
ppdev                   5556  0 
agpgart                32011  1 nvidia
k8temp                  3228  0 
parport_pc             26058  1 
rt2870sta             406690  1 
usblp                  10651  0 
lp                      7342  0 
gameport                9327  4 snd_au8820,ns558
crc_ccitt               1351  1 rt2870sta
asus_atk0110           11423  0 
wacom                  27752  0 
joydev                  8767  0 
parport                31492  3 ppdev,parport_pc,lp
usbhid                 36882  0 
hid                    67742  1 usbhid
firewire_ohci          21234  0 
firewire_core          46643  1 firewire_ohci
sata_nv                19420  5 
forcedeth              49433  0 
crc_itu_t               1383  1 firewire_core
pata_amd                8746  0 


```

---

