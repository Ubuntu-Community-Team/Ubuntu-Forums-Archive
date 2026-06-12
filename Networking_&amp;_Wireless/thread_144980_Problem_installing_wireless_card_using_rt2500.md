---
title: "Problem installing wireless card using rt2500"
date: 2006-03-15
forum: Networking &amp; Wireless
---

### Post by burns on 2006-03-15
Hi.  I got an edimax EW-7128g today which supposedly uses the rt2500 chipset.  However it's not been detected at all.  I've tried installing the drivers following the instructions on the wiki and it all seems to work and the module inserts properly.  But the card isn't listed under ifconfig.  When I do lsmod it returns among other things```
Module                  Size  Used by
rt2500                151012  0

```
I assume it should be used by something?  Has any one got any ideas what to try next, I'm a bit new to this:D.

---

### Post by DarthMandeep on 2006-03-15
What does lspci say about your hardware?

---

### Post by burns on 2006-03-15
```
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 02)
0000:00:07.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:0b.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 40)
0000:00:0c.0 Network controller: RaLink: Unknown device 0301
0000:01:00.0 VGA compatible controller: Matrox Graphics, Inc. MGA G100 [Productiva] AGP (rev 02)
```
So the network card is there, but why unknown device?

---

### Post by burns on 2006-03-19
Has anyone got anymore thoughts on this as I'm still at a total loss:(.

---

