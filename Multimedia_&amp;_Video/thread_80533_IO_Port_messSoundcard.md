---
title: "I/O Port mess/Soundcard"
date: 2005-10-22
forum: Multimedia &amp; Video
---

### Post by Redoute on 2005-10-22
Hi,

my sound card doesn't work any more, probably since the upgrade to Breezy. dmesg contains

4294710.341000] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[4294710.341000] PCI: Unable to reserve I/O region #1:100@de00 for device 0000:00:0c.0
[4294710.341000] ACPI: PCI interrupt for device 0000:00:0c.0 disabled
[4294710.341000] C-Media PCI: probe of 0000:00:0c.0 failed with error -16

and /proc/ioports

```
de00-deff : 0000:00:0c.0
  de00-de03 : motherboard
    de00-de03 : pnp 00:00
```

This is my soundcard (Genius Sound Maker Value 5.1):

0000:00:0c.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
        Subsystem: C-Media Electronics Inc CMI8738/C3DX PCI Audio Device
        Flags: medium devsel, IRQ 10
        I/O ports at de00 [size=256]
        Capabilities: [c0] Power Management version 2

Any solutions?

---

### Post by Redoute on 2005-10-23
Hi,

the problem ist solved by BIOS Update.

For the archives: Motherboard Gigabyte 7IXE4, old BIOS F7 from 2000/08/21, new BIOS Fad from 2002/02/20.

Thanks, Redoute!

---

