---
title: "Rosegarden/JACK with OSS?"
date: 2010-04-05
forum: Multimedia Software
---

### Post by electricmudgenerator on 2010-04-05
Hi all,

Got some queries. I'm running Ubuntu 9.10, with an MAudio Delta 410 PCI soundcard. I wasn't having any luck with audio output on it with ALSA, so have switched to OSS and am now able to hear audio through RhythmBox (alsamixer or envy24control were not even showing up any output on their VDUs).

My next query is with Rosegarden, which I am wanting to use to record and sequence audio. I am new to it but am of the understanding that JACK is required to utilise any audio and MIDI functionality within it. At the moment, when I load Jack, I am getting the following error:

[I]10:51:43.005 Could not open ALSA sequencer as a client. ALSA MIDI patchbay will be not available.
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory[/I]

As such Rosegarden is not functioning, saying "Sound and Audio will not be available for this session".

Could anyone provide any advice regarding where I'm going wrong here?

---

### Post by cchhrriiss121212 on 2010-04-05
You should not need to use OSS with a fully supported alsa card. I have a card with the same chip type and it works fine with alsa/jack. Did you set the analogue volume levels with envy24?

Firstly you will need to get jack running, then you can try using rosegarden. Jack is essential for audio work on linux, and is great once you get it going. Could you post what jack settings are you using? The easiest way to do this is to start jack up then open jackdrc which is a hidden config file in the home folder.

---

### Post by electricmudgenerator on 2010-04-05
OK. I'm rid of OSS and back to ALSA now.

Got Envy24Control up:

Monitor Outputs - PCM Outs 1 and 2 are up, unmuted and set as L/R Gangs
Patchbay - Tried setting the two outputs to both PCM Out as well as Digital Mix
Analog Volume - I have set all DACs/ADCs past the 150 mark.

No audio output at all though.

In the 'Preferences - Sound' section I have the device enabled but there only seem to be digital outputs in the list of outputs. Could that be connected?

---

### Post by cchhrriiss121212 on 2010-04-05
Ubuntu uses pulse audio by default, and it is awful with this type of card (and many others) as it will not recognise anything correctly. Pulse is also fairly redundant for audio production.

You should switch your sound preferences in everything to alsa if you have not done so already. On my system, I uninstall the major pulse packages in synaptic, but you may want to keep it.
The lack of sound could just be that you are not part of the audio group, which you can change in system>users & groups. It takes a log out for that to take effect.

If you still have no sound could you display output for "aplay -l" and "lspci -v"?

---

### Post by electricmudgenerator on 2010-04-06
Thank you for your advice you're providing here Chris.

One thing I've noticed is that my "Sound" box under Preferences, it does not give me the option to assign to Alsa and looks very different to the screenshots I've seen that you described in your last post. The tabs are available: Sound Effects, Hardware, Input, Output, Applications.

I am a member of the Audio group.

**aplay -l**

> **** List of PLAYBACK Hardware Devices ****
card 0: M410 [M Audio Delta 410], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0**lspci -v**

> 00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
    Subsystem: Biostar Microtech Int'l Corp Device 3402
    Flags: bus master, 66MHz, fast devsel, latency 0
    Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
    Subsystem: Biostar Microtech Int'l Corp Device 3402
    Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
    Subsystem: Biostar Microtech Int'l Corp Device 3402
    Flags: 66MHz, fast devsel, IRQ 10
    I/O ports at ff00 [size=32]
    I/O ports at 4c00 [size=64]
    I/O ports at 4c40 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: nForce2_smbus
    Kernel modules: i2c-nforce2

00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2) (prog-if 10)
    Subsystem: Biostar Microtech Int'l Corp Device 3402
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
    Memory at febff000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3) (prog-if 20)
    Subsystem: Biostar Microtech Int'l Corp Device 3402
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at febfe000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
    Subsystem: Biostar Microtech Int'l Corp Device 8204
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    I/O ports at ea00 [size=256]
    I/O ports at ee00 [size=256]
    Memory at febfd000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev a2) (prog-if 8a [Master SecP PriP])
    Subsystem: Biostar Microtech Int'l Corp Device 3402
    Flags: bus master, 66MHz, fast devsel, latency 0
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
    I/O ports at fb00 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_amd

00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3) (prog-if 85 [Master SecO PriO])
    Subsystem: Biostar Microtech Int'l Corp Device 5401
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    I/O ports at 09f0 [size=8]
    I/O ports at 0bf0 [size=4]
    I/O ports at 0970 [size=8]
    I/O ports at 0b70 [size=4]
    I/O ports at f600 [size=16]
    Memory at febfb000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: sata_nv

00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3) (prog-if 85 [Master SecO PriO])
    Subsystem: Biostar Microtech Int'l Corp Device 5401
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    I/O ports at 09e0 [size=8]
    I/O ports at 0be0 [size=4]
    I/O ports at 0960 [size=8]
    I/O ports at 0b60 [size=4]
    I/O ports at f100 [size=16]
    Memory at febfa000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: sata_nv

00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2) (prog-if 01)
    Flags: bus master, 66MHz, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fb000000-fdffffff
    Prefetchable memory behind bridge: d0000000-dfffffff

00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
    Subsystem: Biostar Microtech Int'l Corp Device 2501
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    Memory at febf9000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at f000 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fea00000-feafffff
    Prefetchable memory behind bridge: 00000000fe900000-00000000fe9fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: fe800000-fe8fffff
    Prefetchable memory behind bridge: 00000000fe700000-00000000fe7fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: fe600000-fe6fffff
    Prefetchable memory behind bridge: 00000000fe500000-00000000fe5fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 00009000-00009fff
    Memory behind bridge: fe400000-fe4fffff
    Prefetchable memory behind bridge: 00000000fe300000-00000000fe3fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
    Flags: fast devsel
    Kernel driver in use: k8temp
    Kernel modules: k8temp

01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
    Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 18
    Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
    [virtual] Expansion ROM at fd000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nvidiafb

01:07.0 Network controller: RaLink RT2561/RT61 802.11g PCI
    Subsystem: SiteCom Europe BV Device 90ab
    Flags: bus master, slow devsel, latency 32, IRQ 19
    Memory at fdff8000 (32-bit, non-prefetchable) [size=32K]
    Capabilities: <access denied>
    Kernel driver in use: rt61pci
    Kernel modules: rt61pci

01:08.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
    Subsystem: VIA Technologies Inc. Device d638
    Flags: bus master, medium devsel, latency 32, IRQ 16
    I/O ports at df00 [size=32]
    I/O ports at de00 [size=16]
    I/O ports at dd00 [size=16]
    I/O ports at dc00 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: ICE1712
    Kernel modules: snd-ice1712

---

### Post by cchhrriiss121212 on 2010-04-06
Sound>preferences is a part of pulse setup so it will be no help, I should have mentioned that. You do need to disable your onboard sound from your bios menu (press f2 before grub loads).

---

