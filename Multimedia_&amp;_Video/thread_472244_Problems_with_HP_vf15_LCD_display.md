---
title: "Problems with HP vf15 LCD display"
date: 2007-06-12
forum: Multimedia &amp; Video
---

### Post by Erdaron on 2007-06-12
I'm running Ubuntu 7.04 (installed from LiveCD) with the latest kernel (2.6.20-16-generic). The monitor is HP pavilion vf15 LCD display. I'm using the on-board VGA controller on my motherboard (Foxconn K7S741GXMG-6L, which uses SiS 741GX chipset).

During bootup, at the point where the Ubuntu loading graphic is supposed to come up, the display gives error "Input signal out of range," and then everything goes dark (display actually goes to sleep), until the login screen.

Relevant output of lspci:
> 01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter


I have tried using an AGP video card (ATI Radeon 9550), which had the reverse problem - "Input signal out of range" appeared at login screen, which made the system completely unusable. I couldn't get it to work at all, so I'm abandoning it until I can at least get the on-board controller working smoothly.

I'm pretty new to Linux, and appreciate all the help :D.

---

