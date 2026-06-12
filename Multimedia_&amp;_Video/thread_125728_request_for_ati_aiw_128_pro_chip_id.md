---
title: "request for ati aiw 128 pro chip id"
date: 2006-02-04
forum: Multimedia &amp; Video
---

### Post by stanwebber on 2006-02-04
i need the chip id from an ati all-in-wonder 128 pro 32mb pci card if someone with such an animal would please oblige.  obtain the id by first identifying the busid with ***lspci***
```
00:00.0 Host bridge: Relience Computer CNB20HE (rev 05)
00:00.1 Host bridge: Relience Computer CNB20HE (rev 05)
**00:02.0 VGA compatible controller: ATI Technologies Inc Rage XL (rev 27)**
00:03.0 System peripheral: Compaq Computer Corporation Advanced System Management Controller
00:0f.0 ISA bridge: Relience Computer: Unknown device 0200 (rev 4f)
00:0f.1 IDE interface: Relience Computer: Unknown device 0211
00:0f.2 USB Controller: Relience Computer: Unknown device 0220 (rev 04)
01:03.0 Ethernet controller: Intel Corporation 82557 [Ethernet Pro 100] (rev 08)
01:04.0 Ethernet controller: Intel Corporation 82557 [Ethernet Pro 100] (rev 08)
01:05.0 IDE interface: CMD Technology Inc: Unknown device 0649 (rev 02)
```
then please copy & paste the corresponding entry with ***lspci -n***
```
00:00.0 Class 0600: 1166:0009 (rev 05)
00:00.1 Class 0600: 1166:0009 (rev 05)
**00:02.0 Class 0300: 1002:4752 (rev 27)**
00:03.0 Class 0880: 0e11:a0f0
00:0f.0 Class 0601: 1166:0200 (rev 4f)
00:0f.1 Class 0101: 1166:0211
00:0f.2 Class 0c03: 1166:0220 (rev 04)
01:03.0 Class 0200: 8086:1229 (rev 08)
01:04.0 Class 0200: 8086:1229 (rev 08)
01:05.0 Class 0101: 1095:0649 (rev 02)
```

---

### Post by pumuckly on 2008-05-09
> **stanwebber said:**
> i need the chip id from an ati all-in-wonder 128 pro 32mb pci card if someone with such an animal would please oblige.  obtain the id by first identifying the busid with ***lspci***

then please copy & paste the corresponding entry with ***lspci -n***
```

```

Hi!
I have Ati All-In-Wonder 128 32MB AGP video card (with Rage128 chipset). On developer sites I saw maybe PRO.
Here is **lspci** result:
```

01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 RF/SG AGP

```

And here is the **lspci -n** result (only for videocard):
```

01:00.0 0300: 1002:5246

```

The output of **lspci -vn**. The videocard memory only 32MB. On Motherboard BIOS I set to 64MB for AGP because previously I use Windows and not works with 32MB BIOS settings. I didn't try to set 32MB on Linux at the moment.
```

01:00.0 0300: 1002:5246 (prog-if 00 [VGA controller])
        Subsystem: 1002:0028
        Flags: bus master, VGA palette snoop, stepping, 66MHz, medium devsel, latency 32, IRQ 10
        Memory at d4000000 (32-bit, prefetchable) [size=64M]
        I/O ports at d000 [size=256]
        Memory at d9000000 (32-bit, non-prefetchable) [size=16K]
        [virtual] Expansion ROM at d8000000 [disabled] [size=128K]
        Capabilities: [50] AGP version 2.0
        Capabilities: [5c] Power Management version 1


```

---

