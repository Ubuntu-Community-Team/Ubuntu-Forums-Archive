---
title: "No Sound (Nvidia CK8S)"
date: 2008-01-16
forum: Multimedia &amp; Video
---

### Post by freewaybear on 2008-01-16
I found another thread for the same problem, but he has digital output, I don't (far as I know)[http://ubuntuforums.org/showthread.php?t=502236](http://ubuntuforums.org/showthread.php?t=502236)

I double-checked all my settings (sound properties, alsa mixer, bios, etc.) My media player levels go up and down, so it's playing, but no sound. It gives every indication that there should be sound, but there's none.  :(

heres some info: 

aplay -l:
**** List of PLAYBACK Hardware Devices ****
card 0: CK8S [NVidia CK8S], device 0: Intel ICH [NVidia CK8S]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK8S [NVidia CK8S], device 2: Intel ICH - IEC958 [NVidia CK8S - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

 lspci -v:

00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
        Subsystem: Elitegroup Computer Systems Unknown device 3401
        Flags: bus master, 66MHz, fast devsel, latency 0
        Memory at d0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
        Subsystem: Elitegroup Computer Systems Unknown device 3401
        Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
        Subsystem: Elitegroup Computer Systems Unknown device 3401
        Flags: 66MHz, fast devsel, IRQ 5
        I/O ports at e400 [size=32]
        I/O ports at 4c00 [size=64]
        I/O ports at 4c40 [size=64]
        Capabilities: <access denied>

00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1) (prog-if 10 [OHCI])
        Subsystem: Elitegroup Computer Systems Unknown device 3401
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at ea003000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1) (prog-if 10 [OHCI])
        Subsystem: Elitegroup Computer Systems Unknown device 3401
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        Memory at ea004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2) (prog-if 20 [EHCI])
        Subsystem: Elitegroup Computer Systems Unknown device 3401
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
        Memory at ea005000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
        Subsystem: Elitegroup Computer Systems Unknown device 2501
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at ea000000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at b800 [size=8]
        Capabilities: <access denied>

00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)
        Subsystem: Elitegroup Computer Systems Unknown device aa2e
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
        I/O ports at bc00 [size=256]
        I/O ports at c000 [size=128]
        Memory at ea001000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2) (prog-if 8a [Master SecP PriP])
        Subsystem: Elitegroup Computer Systems Unknown device 3401
        Flags: bus master, 66MHz, fast devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at f000 [size=16]
        Capabilities: <access denied>

00:0a.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2) (prog-if 85 [Master SecO PriO])
        Subsystem: Elitegroup Computer Systems Unknown device 5400
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        I/O ports at 09f0 [size=8]
        I/O ports at 0bf0 [size=4]
        I/O ports at 0970 [size=8]
        I/O ports at 0b70 [size=4]
        I/O ports at dc00 [size=16]
        I/O ports at e000 [size=128]
        Capabilities: <access denied>

00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 16
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=10
        Memory behind bridge: d8000000-dfffffff
        Prefetchable memory behind bridge: e0000000-e7ffffff

00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=128
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: e8000000-e9ffffff
        Prefetchable memory behind bridge: 60000000-600fffff

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel

01:00.0 VGA compatible controller: nVidia Corporation NV20 [GeForce3 Ti 200] (rev a3) (prog-if 00 [VGA])
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 20
        Memory at d8000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (32-bit, prefetchable) [size=64M]
        Memory at e4000000 (32-bit, prefetchable) [size=512K]
        [virtual] Expansion ROM at e4080000 [disabled] [size=64K]
        Capabilities: <access denied>

02:06.0 Ethernet controller: VIA Technologies, Inc. VT86C100A [Rhine] (rev 06)
        Subsystem: D-Link System Inc DFE-530TX rev A
        Flags: bus master, medium devsel, latency 32, IRQ 19
        I/O ports at a000 [size=128]
        Memory at e9000000 (32-bit, non-prefetchable) [size=128]
        [virtual] Expansion ROM at 60000000 [disabled] [size=64K]


I'm at a loss :confused:

---

### Post by freewaybear on 2008-01-17
Anybody have any insight? I've already read through several other similar posts with no luck:(

---

### Post by alterpinguin on 2008-01-17
i can only tell you it works for me:
lspci | grep nVidia
00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2)
00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)
00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2)
00:0a.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600/GeForce 6600 GT] (rev a2)

aplay -l
**** Liste von PLAYBACK Geräten ****
Karte 0: AudioPCI [Ensoniq AudioPCI], Gerät 0: ES1371/1 [ES1371 DAC2/ADC]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
Karte 0: AudioPCI [Ensoniq AudioPCI], Gerät 1: ES1371/2 [ES1371 DAC1]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
Karte 1: CK8S [NVidia CK8S], Gerät 0: Intel ICH [NVidia CK8S]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
Karte 1: CK8S [NVidia CK8S], Gerät 2: Intel ICH - IEC958 [NVidia CK8S - IEC958]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0

----- i use 2 sound-devices, onboard and a pci-card


cat /proc/asound/cards
 0 [AudioPCI       ]: ENS1371 - Ensoniq AudioPCI
                      Ensoniq AudioPCI ENS1371 at 0xc880, irq 19
 1 [CK8S           ]: NFORCE - NVidia CK8S
                      NVidia CK8S with ALC850 at 0xfebfb000, irq 18

and i use the 32-bit linux system, but if i remember right, sound did work with an 64-bit gentoo-system some time ago too. - About Ubuntu, the life-system did initialize the soundcard too, maybe you try the 32-bit install-cd and test the life-system on it. And check your different output-sockets of the onboard sound (head-phones ..).

---

### Post by freewaybear on 2008-01-17
Thank you for your reply. :)

Actually, I am using the 32 bit version of Gutsy (my processor is a Sempron 2600+, so for some reason it shows up as AMD64/Opteron), and I have checked all the jacks. Funny thing is, if I turn the volume up, I can heard the background "hiss" get louder, so it seems like the sound should be working, but it's not, not even system sounds. I know my speakers work (using them right now on another computer) I may just have to buy a cheap soundcard to get sound, but I'd rather not, since I've been out of work since September (broken leg):(

---

### Post by freewaybear on 2008-01-19
I found an old Audigy card in the 'ol parts pile out in the garage, so I'm not even going to pursue this anymore :grin: Thanks anyway, but I'm taking the easy way out this time :grin:

---

