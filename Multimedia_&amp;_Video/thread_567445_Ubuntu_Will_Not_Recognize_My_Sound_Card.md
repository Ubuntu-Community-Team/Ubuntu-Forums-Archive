---
title: "Ubuntu Will Not Recognize My Sound Card"
date: 2007-10-04
forum: Multimedia &amp; Video
---

### Post by VincentValentine on 2007-10-04
I am using Kubuntu 7.04 and I have no sound whatsoever.

 I have an on-board sound card which is enabled in the BIOS, and I have an old Sound Blaster CT4170 that I installed when I could not get Ubuntu to work with the on board card. 

Kubuntu will not even recognize either card.

Any help anyone could offer would be greatly appreciated!

Thank you!!!

---

### Post by Lord Illidan on 2007-10-04
Can you open a terminal, and copy the output of lspci and paste it here?

---

### Post by kellemes on 2007-10-04
Does this help?
[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449&highlight=alsaconf")

---

### Post by VincentValentine on 2007-10-04
When I put lspci in the terminal, here is the output:

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:0e.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
00:11.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 24)
01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)



Thanks for sending the link to the "Comprehensive Sound Problem Solutions Guide", However, I have tried the steps listed there, and I can't get my card to come up... Thanks though...

---

