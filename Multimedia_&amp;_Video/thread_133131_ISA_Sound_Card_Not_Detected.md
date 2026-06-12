---
title: "ISA Sound Card Not Detected"
date: 2006-02-19
forum: Multimedia &amp; Video
---

### Post by rmckay on 2006-02-19
I've had this problem since 5.04, I can't get my ISA sound card to be detected, I know it's a creative but don't know exactly what it is. Ubuntu knows there is ISA, but can't find the sound card.

---

### Post by az on 2006-02-19
[QUOTE=rmckay]I've had this problem since 5.04, I can't get my ISA sound card to be detected, I know it's a creative but don't know exactly what it is. Ubuntu knows there is ISA, but can't find the sound card.[/QUOTE]
Maybe this will help:
[https://wiki.ubuntu.com/HowToSetupSoundCards](https://wiki.ubuntu.com/HowToSetupSoundCards)

The kernel cannot probe ISA hardware with safety.  You have to do it by hand.

What does lspci say?  You can also look in your bios to see whan the card is - sometimes this information is given out.  Compare with the list and try modprobing away...

---

### Post by rmckay on 2006-02-20
Heres what lspci says:
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 02)
0000:00:07.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:0a.0 SCSI storage controller: Adaptec AHA-7850 (rev 01)
0000:00:0b.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 86C326 5598/6326 (rev c3)

---

### Post by az on 2006-02-20
Does your bios reveal anything?

Try the snd-sb16 module, if you are sure it is a Creative card.

---

