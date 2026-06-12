---
title: "Wireless PCMCIA Card Undetected"
date: 2009-12-21
forum: Networking &amp; Wireless
---

### Post by CameronH on 2009-12-21
I just installed Ubuntu 9.10 on my old Dell Latitude CPx laptop. So far, it's been pretty good, but I can't figure out how to get my wireless card to work. I've searched around quite a bit and haven't been able to figure out what the problem is.

The Wireless Card I have is a SMCWCB-G card, and from what I have read it uses the Atheros driver set. 

Would somebody please help me get this working?



> 
**lspcmcia**
Socket 0 Bridge:        [yenta_cardbus]         (bus ID: 000:00:03.0)
Socket 1 Bridge:        [yenta_cardbus]         (bus ID: 000:00:03.1)

**lspci**
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:03.0 CardBus bridge: Texas Instruments PCI1225 (rev 01)
00:03.1 CardBus bridge: Texas Instruments PCI1225 (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:08.0 Multimedia audio controller: ESS Technology ES1978 Maestro 2E (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)


---

### Post by linux6994 on 2009-12-21
I had troubles with wireless on 9.1 and switched to Linux Mint Helena which is KArmic based and all wireless worked well. Just an Idea.

---

### Post by CameronH on 2009-12-22
I may give that a shot, does anyone else have suggestions?

---

