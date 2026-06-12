---
title: "No Sound Difficulties"
date: 2009-08-20
forum: Multimedia Software
---

### Post by KalebSzabo on 2009-08-20
I completed the guide and found both my on-board sound and sound card. I disabled my on-board to use the sound card. I have no idea what my problems are. Here what I got from the guide. (Also nothing is muted. I hear the test sounds but nothing when I got to youtube.)

[COLOR=Red]**** List of PLAYBACK Hardware Devices ****[/COLOR]
[COLOR=Blue] card 0: CMI8738 [C-Media CMI8738], device 0: CMI8738-MC6 [C-Media PCI DAC/ADC][/COLOR]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
[COLOR=Blue] card 0: CMI8738 [C-Media CMI8738], device 1: CMI8738-MC6 [C-Media PCI 2nd DAC][/COLOR]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[COLOR=Blue] card 0: CMI8738 [C-Media CMI8738], device 2: CMI8738-MC6 [C-Media PCI IEC958][/COLOR]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[COLOR=Blue] card 1: au8830 [Aureal Vortex au8830], device 0: AU88x0 ADB [adb][/COLOR]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
[COLOR=DarkOrchid]   <Edited out to shorten list>[/COLOR]
  Subdevice #31: subdevice #31
[COLOR=Blue] card 1: au8830 [Aureal Vortex au8830], device 1: AU88x0 SPDIF [spdif][/COLOR]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[COLOR=Blue] card 1: au8830 [Aureal Vortex au8830], device 2: AU88x0 A3D [a3d][/COLOR]
  Subdevices: 16/16
  Subdevice #0: subdevice #0
[COLOR=DarkOrchid]   <Edited out to shorten list>[/COLOR]
  Subdevice #15: subdevice #15
[COLOR=RoyalBlue] card 1: au8830 [Aureal Vortex au8830], device 3: AU88x0 WT [wt][/COLOR]
  Subdevices: 64/64
  Subdevice #0: subdevice #0
[COLOR=DarkOrchid]  <Edit again>[/COLOR]
  Subdevice #63: subdevice #63
[COLOR=Red] kaleb@kaleb-desktop:~$ lspci -v[/COLOR]
[COLOR=RoyalBlue]00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
    Subsystem: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
    Flags: bus master, 66MHz, medium devsel, latency 8
    Memory at d0000000 (32-bit, prefetchable) [size=128M]
    Capabilities: <access denied>
    Kernel driver in use: agpgart-via
    Kernel modules: via-agp[/COLOR]

[COLOR=SeaGreen]00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
    Flags: bus master, 66MHz, medium devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Memory behind bridge: e0000000-e1ffffff
    Prefetchable memory behind bridge: d8000000-dfffffff
    Capabilities: <access denied>
    Kernel modules: shpchp[/COLOR]

[COLOR=RoyalBlue]00:0a.0 Ethernet controller: Lite-On Communications Inc LNE100TX [Linksys EtherFast 10/100] (rev 25)
    Subsystem: Lite-On Communications Inc Device c001
    Flags: bus master, stepping, medium devsel, latency 32, IRQ 11
    I/O ports at d000 [size=256]
    Memory at e2050000 (32-bit, non-prefetchable) [size=256]
    [virtual] Expansion ROM at 50000000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: tulip
    Kernel modules: tulip[/COLOR]

[COLOR=SeaGreen]00:0b.0 Multimedia audio controller: Aureal Semiconductor Vortex 2 (rev fe)
    Subsystem: Aureal Semiconductor Device 0088
    Flags: bus master, medium devsel, latency 32, IRQ 5
    Memory at e2000000 (32-bit, non-prefetchable) [size=256K]
    I/O ports at d400 [size=8]
    I/O ports at d800 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: au8830
    Kernel modules: snd-au8830[/COLOR]

[COLOR=RoyalBlue]00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
    Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
    Flags: bus master, medium devsel, latency 32, IRQ 10
    I/O ports at dc00 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd[/COLOR]

[COLOR=SeaGreen]00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
    Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
    Flags: bus master, medium devsel, latency 32, IRQ 11
    I/O ports at e000 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd[/COLOR]

[COLOR=RoyalBlue]00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
    Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
    Flags: bus master, medium devsel, latency 32, IRQ 5
    I/O ports at e400 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd[/COLOR]

[COLOR=SeaGreen]00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82) (prog-if 20)
    Subsystem: VIA Technologies, Inc. USB 2.0
    Flags: bus master, medium devsel, latency 32, IRQ 12
    Memory at e2051000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>[/COLOR]
    [COLOR=SeaGreen]Kernel driver in use: ehci_hcd[/COLOR]

[COLOR=RoyalBlue]00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
    Subsystem: VIA Technologies, Inc. VT8235 ISA Bridge
    Flags: bus master, stepping, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: i2c-viapro, via-ircc[/COLOR]

[COLOR=SeaGreen]00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
    Subsystem: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
    Flags: bus master, medium devsel, latency 32, IRQ 10
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
    I/O ports at e800 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_via
[/COLOR] [COLOR=RoyalBlue]
00:14.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
    Subsystem: Chaintech Computer Co. Ltd Device 1100
    Flags: bus master, medium devsel, latency 32, IRQ 12
    I/O ports at ec00 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: C-Media PCI
    Kernel modules: snd-cmipci[/COLOR]

[COLOR=SeaGreen]01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a2)
    Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 10
    Memory at e0000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d8000000 (32-bit, prefetchable) [size=128M]
    [virtual] Expansion ROM at e1000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nvidiafb
//End List[/COLOR]

Help?

---

### Post by j.bell730 on 2009-08-20
So is YouTube the only thing you're not getting audio from? If so, that's quite an [easy fix]("http://ubuntuforums.org/showpost.php?p=5678390&postcount=9").

---

