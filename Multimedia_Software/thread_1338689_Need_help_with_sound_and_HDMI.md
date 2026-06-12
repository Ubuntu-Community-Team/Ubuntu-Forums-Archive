---
title: "Need help with sound and HDMI"
date: 2009-11-26
forum: Multimedia Software
---

### Post by Celticdale on 2009-11-26
Hello,

This is my first post. I'll try my best to explain my problem. 

I have a HP VoodooDNA 802. It has two NVidia 9800S SLI cards (one DVI output) and a HDMI output. I installed the 64 bit version of Ubuntu and everything went well. Everything is updated and it runs well EXCEPT for the sound. This computer has an onboard soundcard with an optical and analog output. Neither of which I can get any sound out of. The sound appears to be coming out of the HDMI subsystem. No matter what I choose in the control panel allows me to choose the analog output. Only the HDMI works. The HDMI output sounds like it's coming out of the onboard speaker. I've checked to see if the mixer has the channel muted, it does not. 

This is my aplay -L output:

```
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    Playback/recording through the PulseAudio sound server
```I can turn up the sound and hear things but I want the sound to come out either the analog output or thru the DVI cable (Like it does for Windows). The DVI connection I have goes from DVI to HDMI (at the monitor). I know it works in Windows. 

I'm not sure if I can just hook-up a HDMI to HDMI and get the sound. I'm concerned that if I do that, my video performance will suffer. I don't know if that's true or not. 

This is my lspci output:
```

00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
    Subsystem: Hewlett-Packard Company Device 2a83
    Flags: bus master, 66MHz, fast devsel, latency 0

00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
    Subsystem: Hewlett-Packard Company Device 2a83
    Flags: bus master, 66MHz, fast devsel, latency 0

00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
    Subsystem: Hewlett-Packard Company Device 2a83
    Flags: bus master, 66MHz, fast devsel, latency 0
    I/O ports at 4f00 [size=256]

00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
    Subsystem: Hewlett-Packard Company Device 2a83
    Flags: 66MHz, fast devsel

00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
    Subsystem: Hewlett-Packard Company Device 2a83
    Flags: 66MHz, fast devsel, IRQ 11
    I/O ports at 4900 [size=64]
    I/O ports at 4d00 [size=64]
    I/O ports at 4e00 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: nForce2_smbus
    Kernel modules: i2c-nforce2

00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
    Subsystem: Hewlett-Packard Company Device 2a83
    Flags: 66MHz, fast devsel

00:03.4 RAM memory: nVidia Corporation Device 0a98 (rev b1)
    Subsystem: Hewlett-Packard Company Device 2a83
    Flags: 66MHz, fast devsel

00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
    Subsystem: Hewlett-Packard Company Device 2a83
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 9
    Memory at f1e80000 (32-bit, non-prefetchable) [size=512K]

00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1) (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 2a83
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    Memory at f1e7f000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1) (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 2a83
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
    Memory at f1e7ec00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1) (prog-if 10)
    Subsystem: nVidia Corporation Device cb79
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at f1e7d000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1) (prog-if 20)
    Subsystem: nVidia Corporation Device cb79
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    Memory at f1e7e800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
    Subsystem: nVidia Corporation Device cb84
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    Memory at f1e78000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1) (prog-if 01)
    Flags: bus master, 66MHz, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
    Memory behind bridge: f1f00000-f1ffffff
    Capabilities: <access denied>

00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
    Subsystem: Hewlett-Packard Company Device 2a83
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
    Memory at f1e7c000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at a080 [size=8]
    Memory at f1e7e400 (32-bit, non-prefetchable) [size=256]
    Memory at f1e7e000 (32-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

00:0b.0 SATA controller: nVidia Corporation MCP79 AHCI Controller (rev b1) (prog-if 01)
    Subsystem: Hewlett-Packard Company Device 2a83
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 30
    I/O ports at a000 [size=8]
    I/O ports at 9c00 [size=4]
    I/O ports at 9880 [size=8]
    I/O ports at 9800 [size=4]
    I/O ports at 9480 [size=16]
    Memory at f1e76000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: f2000000-f5ffffff
    Prefetchable memory behind bridge: 00000000b0000000-00000000bfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:0d.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: f6000000-faefffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: faf00000-fbffffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000edffffff
    Capabilities: <access denied>
    Kernel modules: shpchp

00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=09, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fe000000-febfffff
    Prefetchable memory behind bridge: 00000000ee000000-00000000f0ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:18.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

01:07.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70) (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 2a83
    Flags: bus master, medium devsel, latency 32, IRQ 19
    Memory at f1fff000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

02:00.0 VGA compatible controller: nVidia Corporation Device 062f (rev a1)
    Subsystem: nVidia Corporation Device 060e
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at f5000000 (32-bit, non-prefetchable) [size=16M]
    Memory at b0000000 (64-bit, prefetchable) [size=256M]
    Memory at f2000000 (64-bit, non-prefetchable) [size=32M]
    I/O ports at bc00 [size=128]
    [virtual] Expansion ROM at f4f80000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nvidiafb

03:00.0 VGA compatible controller: nVidia Corporation Device 062f (rev a1)
    Subsystem: nVidia Corporation Device 060e
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f9000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at f6000000 (64-bit, non-prefetchable) [size=32M]
    I/O ports at cc00 [size=128]
    [virtual] Expansion ROM at fae80000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nvidiafb

04:00.0 VGA compatible controller: nVidia Corporation C79 [nForce 760i SLI] (rev b1)
    Subsystem: Hewlett-Packard Company Device 2a83
    Flags: bus master, fast devsel, latency 0, IRQ 23
    Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at ec000000 (64-bit, prefetchable) [size=32M]
    I/O ports at dc00 [size=128]
    [virtual] Expansion ROM at fafe0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nvidiafb
```I'll check digging around but I'm hoping there's an easy answer to this, somewhere. 

Cheers,

-Dale

---

### Post by yonghokim on 2009-12-05
hey, this is an unrelated question.. i'm looking forward to buy the firebird as well. does dual monitor work on ubuntu? one monitor on dvi, another monitor on hdmi. what about two monitors of different proportions? like one 4:3 ratio 17", and another 21" widescreen.

---

