---
title: "Use chipset instead of videocard"
date: 2010-08-28
forum: Multimedia Software
---

### Post by seahorsepip on 2010-08-28
Ok heres what I got:
-Intel 8294 Expres Chipset Famely (On Motherboard) (Output: VGA Only!)
-Nvidia GT 220 (PCI) (Output: DVI & VGA)
-HP 2310ti/t Monitor (Resolution: 1920x1080, Input: DVI & VGA)

What I want to do:
I want to use the intel for linux so I can have 3D support and a working plymouth.

So how I wanted to do it: use settings on linux to use intel at burg/grub2 and linux itself(plymouth&system) and set windows to use nvidia gt 220  by settings and drivers.
I need to connect the VGA port of the monitor and the intel chipset with each other and the DVI port of the monitor with the Videocard.

Problem:
The connections of the inputs and outputs are already connected with cables so thats done but...What do I need to change in My Ubuntu 10.04 32Bit to activate and use the Intel chipset instead of the Nvidia Card:confused:

if it all works it will be a crazy way to get still full support for games at windows and linux with drivers of the chipset.(The monitor can autochange to the right input so that is all automatic without problems)

Btw I got 4 years experience with Ubuntu so don look at my amount of beans...I just never used this forum I use normaly other forums...)

---

### Post by analystscouch on 2010-09-15
I want to do essentially the same thing in 10.04.

My motherboard is a G33 chipset with onboard video. I also have an nVidia GTX 260 plugged into a PCI-E slot.

Both of these output to the *same* monitor, the nVidia via HDMI and the onboard via VGA.

In Windows I have disabled the onboard video so that output is only via the nVidia card. What i'm hoping to do is disable the nVidia card altogether in Ubuntu, so that I can output via onboard video only. Any help would be greatly appreciated.

Thanks,
Nick

---

### Post by Yellow Pasque on 2010-09-15
> **analystscouch said:**
> I want to do essentially the same thing in 10.04.

My motherboard is a G33 chipset with onboard video. I also have an nVidia GTX 260 plugged into a PCI-E slot.

Both of these output to the *same* monitor, the nVidia via HDMI and the onboard via VGA.

In Windows I have disabled the onboard video so that output is only via the nVidia card. What i'm hoping to do is disable the nVidia card altogether in Ubuntu, so that I can output via onboard video only. Any help would be greatly appreciated.

Thanks,
Nick
Look in your BIOS for the GPU initialization order.

---

### Post by analystscouch on 2010-09-20
> **Temüjin said:**
> Look in your BIOS for the GPU initialization order.

That worked, thanks.

---

