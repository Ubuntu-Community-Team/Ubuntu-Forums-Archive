---
title: "No SPDIF audio after 9.04 upgrade"
date: 2009-05-26
forum: Multimedia Software
---

### Post by Shiskimalii on 2009-05-26
I was previously using Ubuntu 8.10 with audio through my graphics card (Nvidia 9800 GX2) using onboard SPDIF. My sound card is a Realtek ALC1200. I got this working by using alsamixer to unmute all iec958 channels (I think... cant remember) and running the sound with Pulse Audio. After the upgrade my sound worked fine until I rebooted. I have tried unmuting the iec958 channels again but it has not worked. I have also tried using only alsa. The only thing I can think of that changed is I manually upgraded to the new NVidia provided driver 180 instead of the old 177.

some information

> aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


> aplay -L
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)


> lspci -v
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 82e2
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation MCP78S [GeForce 8200] LPC Bridge (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 82e2
	Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device 82e2
	Flags: 66MHz, fast devsel, IRQ 255
	I/O ports at ff00 [size=64]
	I/O ports at 1c00 [size=64]
	I/O ports at 1c40 [size=64]
	Capabilities: <access denied>

00:01.2 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device 82e2
	Flags: 66MHz, fast devsel

00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 82e2
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
	Memory at fdf80000 (32-bit, non-prefetchable) [size=512K]

00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device 82e2
	Flags: 66MHz, fast devsel

00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 82e2
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1) (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 82e2
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 82e2
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1) (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 82e2
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at fe02c000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. (Wrong ID) Device 82e2
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at fc00 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_amd

00:07.0 Audio device: nVidia Corporation MCP78S [GeForce 8200] High Definition Audio (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device 82fe
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at fe020000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1) (prog-if 01)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fde00000-fdefffff
	Prefetchable memory behind bridge: fdd00000-fddfffff
	Capabilities: <access denied>

00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Device 82e2
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 2299
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at f700 [size=16]
	Memory at fe026000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:0a.0 Ethernet controller: nVidia Corporation MCP78S [GeForce 8200] Ethernet (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 82e2
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 2298
	Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at f600 [size=8]
	Memory at fe02a000 (32-bit, non-prefetchable) [size=256]
	Memory at fe029000 (32-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fb000000-fcffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel modules: shpchp

00:10.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=06, sec-latency=0
	I/O behind bridge: 0000b000-0000cfff
	Memory behind bridge: e2000000-e9ffffff
	Prefetchable memory behind bridge: 00000000b0000000-00000000cfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:12.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: fdc00000-fdcfffff
	Prefetchable memory behind bridge: 00000000fdb00000-00000000fdbfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:13.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: fda00000-fdafffff
	Prefetchable memory behind bridge: 00000000fd900000-00000000fd9fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	I/O behind bridge: 00008000-00008fff
	Memory behind bridge: fd800000-fd8fffff
	Prefetchable memory behind bridge: 00000000fd700000-00000000fd7fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
	Flags: fast devsel

01:0a.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 8294
	Flags: bus master, medium devsel, latency 32, IRQ 19
	Memory at fdeff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

02:00.0 VGA compatible controller: nVidia Corporation GeForce 8300 (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 82e2
	Flags: bus master, fast devsel, latency 0, IRQ 20
	Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=128M]
	Memory at de000000 (64-bit, prefetchable) [size=32M]
	I/O ports at dc00 [size=128]
	[virtual] Expansion ROM at d8000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

03:00.0 PCI bridge: nVidia Corporation PCI express bridge for Quadro Plex S4 / Tesla S870 / Tesla S1070 (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=03, secondary=04, subordinate=06, sec-latency=0
	I/O behind bridge: 0000b000-0000cfff
	Memory behind bridge: e2000000-e9ffffff
	Prefetchable memory behind bridge: 00000000b0000000-00000000cfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

04:00.0 PCI bridge: nVidia Corporation PCI express bridge for Quadro Plex S4 / Tesla S870 / Tesla S1070 (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=04, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: e6000000-e9ffffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

04:02.0 PCI bridge: nVidia Corporation PCI express bridge for Quadro Plex S4 / Tesla S870 / Tesla S1070 (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=04, secondary=06, subordinate=06, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: e2000000-e5ffffff
	Prefetchable memory behind bridge: 00000000b0000000-00000000bfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

05:00.0 3D controller: nVidia Corporation GeForce 9800 GX2 (rev a2)
	Subsystem: nVidia Corporation Device 0504
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at e8000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at e6000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at cc00 [size=128]
	[virtual] Expansion ROM at e9000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

06:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GX2 (rev a2)
	Subsystem: nVidia Corporation Device 0504
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at e4000000 (32-bit, non-prefetchable) [size=16M]
	Memory at b0000000 (64-bit, prefetchable) [size=256M]
	Memory at e2000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at bc00 [size=128]
	[virtual] Expansion ROM at e5fe0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb


---

### Post by ResoMail on 2009-09-06
Have you been able to make your sound card work?

---

### Post by Lost_in_Edmonton on 2009-12-24
I'm having the same issue with 9.10 riding on my Asus P6T Delux board. Using Nvidia driver 185.18.36, with my 9800 gx2.

Has anyone found a solution to this yet?


**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

desktop:~$ aplay -L
front:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, AD198x Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=Headset,DEV=0
    Logitech USB Headset, USB Audio
    Front speakers
surround40:CARD=Headset,DEV=0
    Logitech USB Headset, USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Headset,DEV=0
    Logitech USB Headset, USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Headset,DEV=0
    Logitech USB Headset, USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Headset,DEV=0
    Logitech USB Headset, USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Headset,DEV=0
    Logitech USB Headset, USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Headset,DEV=0
    Logitech USB Headset, USB Audio
    IEC958 (S/PDIF) Digital Audio Output

desktop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation X58 I/O Hub to ESI Port (rev 12)
	Subsystem: ASUSTeK Computer Inc. Device 836b
	Flags: fast devsel
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 (rev 12)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:03.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 12)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=05, sec-latency=0
	I/O behind bridge: 0000a000-0000bfff
	Memory behind bridge: f4000000-fbbfffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:07.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 (rev 12)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:14.0 PIC: Intel Corporation 5520/5500/X58 I/O Hub System Management Registers (rev 12)
	Flags: fast devsel
	Capabilities: <access denied>

00:14.1 PIC: Intel Corporation 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 12)
	Flags: fast devsel
	Capabilities: <access denied>

00:14.2 PIC: Intel Corporation 5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 12)
	Flags: fast devsel
	Capabilities: <access denied>

00:14.3 PIC: Intel Corporation 5520/5500/X58 I/O Hub Throttle Registers (rev 12)
	Flags: fast devsel

00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 9800 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 9880 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 9c00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at f3fff000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
	Subsystem: ASUSTeK Computer Inc. Device 82ea
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f3ff8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	Prefetchable memory behind bridge: 00000000f2f00000-00000000f2ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 3
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fbd00000-fbdfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fbc00000-fbcfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 9080 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 9400 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 9480 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f3ffe000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=32
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fbe00000-fbefffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 54
	I/O ports at 8c00 [size=8]
	I/O ports at 8880 [size=4]
	I/O ports at 8800 [size=8]
	I/O ports at 8480 [size=4]
	I/O ports at 8400 [size=32]
	Memory at f3ffc000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: medium devsel, IRQ 11
	Memory at f3ffd000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 0400 [size=32]
	Kernel modules: i2c-i801

02:00.0 PCI bridge: nVidia Corporation PCI express bridge for Quadro Plex S4 / Tesla S870 / Tesla S1070 (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=02, secondary=03, subordinate=05, sec-latency=0
	I/O behind bridge: 0000a000-0000bfff
	Memory behind bridge: f4000000-fbbfffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel modules: shpchp

03:00.0 PCI bridge: nVidia Corporation PCI express bridge for Quadro Plex S4 / Tesla S870 / Tesla S1070 (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=03, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: f4000000-f7ffffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
	Capabilities: <access denied>
	Kernel modules: shpchp

03:02.0 PCI bridge: nVidia Corporation PCI express bridge for Quadro Plex S4 / Tesla S870 / Tesla S1070 (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=03, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: f8000000-fbbfffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel modules: shpchp

04:00.0 3D controller: nVidia Corporation G92 [GeForce 9800 GX2] (rev a2)
	Subsystem: nVidia Corporation Device 0504
	Flags: bus master, fast devsel, latency 0, IRQ 24
	Memory at f7000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at f4000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at ac00 [disabled] [size=128]
	[virtual] Expansion ROM at f6fe0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

05:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GX2] (rev a2)
	Subsystem: nVidia Corporation Device 0504
	Flags: bus master, fast devsel, latency 0, IRQ 35
	Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at f8000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at bc00 [disabled] [size=128]
	[virtual] Expansion ROM at fbbe0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

07:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
	Subsystem: ASUSTeK Computer Inc. Device 81f8
	Flags: bus master, fast devsel, latency 0, IRQ 56
	Memory at fbcfc000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at c800 [size=256]
	Expansion ROM at fbcc0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: sky2
	Kernel modules: sky2

08:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
	Subsystem: ASUSTeK Computer Inc. Device 81f8
	Flags: bus master, fast devsel, latency 0, IRQ 55
	Memory at fbdfc000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at d800 [size=256]
	Expansion ROM at fbdc0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: sky2
	Kernel modules: sky2

0a:02.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 81fe
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at fbeff000 (32-bit, non-prefetchable) [size=2K]
	I/O ports at ec00 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

---

