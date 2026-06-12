---
title: "Visible noise on right side of display"
date: 2006-09-08
forum: Multimedia &amp; Video
---

### Post by xp_newbie on 2006-09-08
I recently installed Ubuntu 6.0.6 on an old system (PII 350MHz 512MB) and while it works, it has constant noisy lines on the right side of the display (which worsens if I move any window).

The display card is a Matrox G200 AGP and manages to work (in this installation) at a resolution of 1600x1200 @ 85Hz. However, the (visual) noise is pretty annoying.

Any idea how to solve this problem? (it does not exist when I run Windows 2000 on the same exact system).

If the following can be of any help, here is the relevant output from lshw:

>         *-pci
             description: PCI bridge
             product: 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: MGA G200 AGP
                vendor: Matrox Graphics, Inc.
                physical id: 0
                bus info: pci@01:00.0
                version: 01
                size: 16MB
                width: 32 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:e3000000-e3ffffff                    iomemory:e2000000-e2003fff iomemory:e1800000-e1ffffff irq:11


Thanks!
Alex

---

### Post by tseliot on 2006-09-08
Try setting the driver to vesa:
```
sudo dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

then log out and press CTRL+ALT+Backspace.

Then log in

---

### Post by xp_newbie on 2006-09-12
Thanks. I tried that (i.e. vesa), but then it limits my resolution to 1024x768 (and down) only. I reverted back to the previous xorg.conf. If you have another suggestion that would be great.

---

### Post by JacksonDane on 2007-02-13
Having the same problem, no idea what is causing it, only on the right side of windows will it have these wierd lines/noise

---

### Post by xp_newbie on 2007-02-14
> **JacksonDane said:**
> Having the same problem, no idea what is causing it, only on the right side of windows will it have these wierd lines/noise

Apparently, this is a device driver problem for that Matrox graphics card - and that card is too old for Linux developers to invest any work on it.

So, I solved the problem by re-installing Windows 2000 Professional on that machine.

My newer machine, a 3GHz P4 with nVidia graphics chipset works beautifully with Ubuntu 6.06.

---

