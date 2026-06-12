---
title: "Driver help"
date: 2010-03-23
forum: Multimedia Software
---

### Post by Liamjg on 2010-03-23
I just recently installed Ubuntu and am having some trouble driver wise.
Ubuntu doesn't appear to recognise the correct audio device.

Instead of my motherboard's onboard (AC'97) audio, it only finds my GPU's (Radeon HD 4350).

Any help would be greatly appreciated...

---

### Post by themusicalduck on 2010-03-23
Ubuntu doesn't install drivers for your sound, only graphics or wireless. So if you're looking in Administration > Hardware Drivers, then there won't be anything for your soundcard.

The soundcard should just work straight away. Have you checked in your sound preferences in System > Preferences > Sounds to check volume levels and that the right hardware is selected for output and that nothing is muted?

Alternatively, you could open a terminal (Applications > Accessories > Terminal), type in ```
alsamixer
``` and see if there is anything there you can change, like volume.

---

### Post by RedSingularity on 2010-03-23
Do you have sound at all?

---

### Post by Liamjg on 2010-03-23
Nope, none at all. I tried configuring the sound device in the sound preferences menu but found nothing. As before it thinks that my GPU is controlling my sound.

---

### Post by RedSingularity on 2010-03-23
And you looked in alsamixer to check the levels?

---

### Post by Liamjg on 2010-03-23
Yeah, nothing showed up control wise. Would it help if posted a cropped picture of alsamixer?

---

### Post by RedSingularity on 2010-03-23
You dont have to.  Umm post the output of 

aplay -l

---

### Post by Liamjg on 2010-03-23
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by RedSingularity on 2010-03-23
Now post the output of 

lspci -v

---

### Post by Liamjg on 2010-03-23
Ooof this is a along one. Thanks for the help by the way...

```
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
    Subsystem: Hewlett-Packard Company Device 2a26
    Flags: bus master, 66MHz, medium devsel, latency 64
    Kernel modules: ati-agp

00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fdd00000-fddfffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Hewlett-Packard Company Device 2a26
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
    I/O ports at ff00 [size=8]
    I/O ports at fe00 [size=4]
    I/O ports at fd00 [size=8]
    I/O ports at fc00 [size=4]
    I/O ports at fb00 [size=16]
    Memory at fe02f000 (32-bit, non-prefetchable) [size=512]
    Expansion ROM at fdf80000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: sata_sil

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 2a26
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at fe02e000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 2a26
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 2a26
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
    Subsystem: Hewlett-Packard Company Device 2a26
    Flags: 66MHz, medium devsel
    I/O ports at 0b00 [size=16]
    Memory at fe02b000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80) (prog-if 8a [Master SecP PriP])
    Subsystem: Hewlett-Packard Company Device 2a26
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at f900 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_atiixp

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
    Subsystem: Hewlett-Packard Company Device 2a26
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01)
    Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fdc00000-fdcfffff
    Prefetchable memory behind bridge: fde00000-fdefffff

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

01:00.0 VGA compatible controller: ATI Technologies Inc RV710 [Radeon HD 4350]
    Subsystem: XFX Pine Group Inc. Device 2462
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at fdde0000 (64-bit, non-prefetchable) [size=64K]
    I/O ports at ee00 [size=256]
    Expansion ROM at fddc0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon

01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
    Subsystem: XFX Pine Group Inc. Device aa38
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at fddfc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Hewlett-Packard Company Device 2a26
    Flags: bus master, medium devsel, latency 64, IRQ 21
    I/O ports at dc00 [size=256]
    Memory at fdcff000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: 8139too
    Kernel modules: epl, 8139too, 8139cp

02:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80) (prog-if 10)
    Subsystem: Device 0003:000f
    Flags: bus master, stepping, medium devsel, latency 64, IRQ 20
    Memory at fdcfe000 (32-bit, non-prefetchable) [size=2K]
    I/O ports at df00 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

```

---

### Post by RedSingularity on 2010-03-23
I know this sounds obvious but make sure you are not muting the volume.  In alsamixer you should be able to adjust the volume with the up down arrow keys.

---

### Post by Liamjg on 2010-03-23
Still nothing...

---

### Post by RedSingularity on 2010-03-23
In a terminal try this

sudo modprobe snd-atiixp

Then see if you have sound.

---

### Post by Liamjg on 2010-03-23
Still nothing. I had this same problem in WinXP. I was able to fix it by disabling the audio function of the card leaving only my onboard audio.

---

### Post by RedSingularity on 2010-03-23
Did you try that in Ubuntu?

---

### Post by Liamjg on 2010-03-23
Yup. Still nothing.

I'm starting to think that my problem is rather rare...

---

### Post by RedSingularity on 2010-03-23
[Here](http://ubuntuforums.org/showthread.php?t=205449) is an excellent troubleshooting link. 

Try it out.

---

### Post by Liamjg on 2010-03-23
Sorry I put you through that. It was my fault all along.

In my system BIOS onboard audio was set to [AUTO] I guess Ubuntu just had trouble configuring it from there. Changing it to [ENABLED] worked.

Thanks a ton!

---

### Post by RedSingularity on 2010-03-23
Good to hear you got it!  :)

---

