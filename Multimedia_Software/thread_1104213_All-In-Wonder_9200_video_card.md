---
title: "All-In-Wonder 9200 video card"
date: 2009-03-23
forum: Multimedia Software
---

### Post by duke708 on 2009-03-23
Hi there I am somewhat new to ubuntu 8.10 and I have a All-In-Wonder 9200 video card and am having trouble with the TV tuner aspect of the card can anyone help?

---

### Post by artsci2 on 2009-03-24
The AIW series video input is not functional in LINUX. This has something to do with the tuner being onboard the AGP card. Details would have to come from someone more expert than me. There is mention of this on the ATI/AMD web site. 

I have AGP AIW 2006 (9600 series) and PCI-e AIW HD (3650 GPU) and those cards are also unsupported for video input on LINUX.

---

### Post by Em-Buntu on 2009-03-25
You are out of luck with any version of ATI's AIW cards under Linux or any 64-bit Windows because the tuner portion of the board is totally proprietary and ATI/AMD refused to update the drivers and Multimedia Manager Center (MMC) to 64-bits or open the architecture for Linux.
The only way to support any AIW is to use a 32-bit Windows.

---

