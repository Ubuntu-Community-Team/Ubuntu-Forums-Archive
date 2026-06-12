---
title: "Refresh Rate: 0"
date: 2008-12-18
forum: Multimedia Software
---

### Post by simptechmike on 2008-12-18
Previously with Ubuntu 8.0.4 there were refresh rates for my onboard video. However, 8.10 gives only a refresh rate of 0.  How do I get 8.10 to detect my video cards refresh rates?

lspci | grep vga

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter (rev 03)

Monitor is Hyundai ImageQuest L91A

Resolutions supported: 1024 x 768, 1280 x 1024, 640 x 480, 720 x 400, 800 x 600, 832 x 624
Synchronization Range - Vertical: 56 - 75 Hz
Synchronization Range - Horizontal: 31 - 80 kHz

---

### Post by simptechmike on 2008-12-26
Does Ubuntu not autodetect video cards? How can I get my monitor to stop flickering as it appears to be using too high of a refresh rate?

---

