---
title: "Sound lags, while scrolling down a web page"
date: 2009-09-21
forum: Multimedia Software
---

### Post by srulik on 2009-09-21
Hello forum,

I have this somewhat strange sound problem,
whilst using my web-browser (be it Firefox or Epiphany), when I scroll up/down - the sound lags for that period of time.

That means, that while reading an article - I can't listen to music.

Using a Toshiba laptop with 9.04. This is the relevant part of 'lspci':
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)      

Suggestions?
David :)

---

### Post by raboofje on 2009-09-21
Perhaps the audio and video card are sharing some resource - are they on the same IRQ? (see 'lspci -v' and /proc/interrupts)

---

### Post by srulik on 2009-09-24
@[raboofje]("http://ubuntuforums.org/member.php?u=712909")

Here's the /proc/interrupts:
          CPU0       
  0:    6119282   IO-APIC-edge      timer
  1:      23674   IO-APIC-edge      i8042
  8:          1   IO-APIC-edge      rtc0
  9:      46228   IO-APIC-fasteoi   acpi
 12:    2629533   IO-APIC-edge      i8042
 14:     266075   IO-APIC-edge      ata_piix
 15:     222395   IO-APIC-edge      ata_piix
** 16:    1844009   IO-APIC-fasteoi   i915@pci:0000:00:02.0, eth0**
 17:    3460406   IO-APIC-fasteoi   yenta, ath
 18:          0   IO-APIC-fasteoi   uhci_hcd:usb4
 19:          0   IO-APIC-fasteoi   uhci_hcd:usb3
 **21:    2912767   IO-APIC-fasteoi   HDA Intel**
 22:          0   IO-APIC-fasteoi   uhci_hcd:usb5
 23:          0   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb2
NMI:          0   Non-maskable interrupts
LOC:    5397087   Local timer interrupts
RES:          0   Rescheduling interrupts
CAL:          0   Function call interrupts
TLB:          0   TLB shootdowns
SPU:          0   Spurious interrupts
ERR:          0
MIS:          0

Here are relevant excerpts (display\sound only) from 'lspci -v':
root@david-laptop:~# lspci -v
...
00:02.0 **VGA** compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, fast devsel, latency 0, **IRQ 16**
    Memory at ff680000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at ec00 [size=8]
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    Memory at ff640000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Capabilities: [d0] Power Management version 2
    Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, fast devsel, latency 0
    Memory at ff580000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: [d0] Power Management version 2

00:1b.0 **Audio** device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, fast devsel, latency 0, **IRQ 21**
    Memory at ff63c000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [130] Root Complex Link <?>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

...

... IRQ 17 - Ethernet/WiFi ...

05:07.0 **Ethernet** controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, medium devsel, latency 64, **IRQ 16**
    I/O ports at d800 [size=256]
    Memory at ff3ffc00 (32-bit, non-prefetchable) [size=256]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp


It seems like the Ethernet is sitting on both IRQs 16, 17. Thus sharing IRQ 16, with the... Display system.
What that's got to do with me being left without sound!? How could two resources be sharing the same interrupt to begin with?!
Suggestions? Help...

---

