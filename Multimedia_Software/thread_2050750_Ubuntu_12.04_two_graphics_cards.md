---
title: "Ubuntu 12.04 two graphics cards"
date: 2012-08-31
forum: Multimedia Software
---

### Post by chefytim on 2012-08-31
I have been struggling to get my two graphics cards to work. One is on the board and one is not. I can change the BIOS on my MSI motherboard to "Internal, PCI, or PCI-E". Internal of course the one on the board becomes available. If I use PCI or PCI-E the card is used but the internal just doesn't show up at all on the system. With Windows installed "Internal" allows both to work.

Here is what I get when I do a "lspci"

01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS780L [Radeon HD 3000]
02:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV516 [Radeon X1300/X1550 Series]
02:00.1 Display controller: Advanced Micro Devices [AMD] nee ATI RV516 [Radeon X1300 Pro] (Secondary)

I'm not sure why the external, "X1300" is showing up twice.

I have tried to adjust the xorg.conf file which of course is not found initially but I guess I can't get it configured correct as it just crashes the OS or "X" anyway. I have two LG FLATRON W2061TQ monitors.

Any ideas on how to get both cards working with extended displays?

Thanks:guitar:

---

