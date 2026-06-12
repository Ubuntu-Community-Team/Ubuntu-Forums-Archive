---
title: "2nd ATI Video card not coming up"
date: 2012-02-10
forum: Multimedia Software
---

### Post by cdalex on 2012-02-10
Hello, 

I recently installed two identical (cheap) Sapphire (ATI) Radeon 5450 1gb pci-e cards to replace my ATI 5450 512mb card.


[LIST]
[*] Card 1 has a ACER 22"" LCD on the DVI port and a generic 20" monitor on the HDMI port. they both work fine
[*] Card 2 has a ACER 22" LCD on the DVI port and is not showing up in Settings> Displays nor coming on.
[/LIST]
 
Both cards are recognized by Ubuntu:

> [INDENT]oot@Hydra:~# lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Cedar PRO [Radeon HD 5450] [1002:68f9]
02:00.0 VGA compatible controller [0300]: ATI Technologies Inc Cedar PRO [Radeon HD 5450] [1002:68f9]
root@Hydra:~# lshw -C display
  *-display               
       description: VGA compatible controller
       product: Cedar PRO [Radeon HD 5450]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:49 memory:c0000000-cfffffff memory:fbbc0000-fbbdffff ioport:a000(size=256) memory:fbba0000-fbbbffff
  *-display
       description: VGA compatible controller
       product: Cedar PRO [Radeon HD 5450]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:50 memory:d0000000-dfffffff memory:fbcc0000-fbcdffff ioport:b000(size=256) memory:fbca0000-fbcbffff
[/INDENT]I have poked around on the web and found plenty on nvidia cards, but not much on ATI. I do UNIX for a living but I am a shell/CLI guy and video is not my forte. Could someone point me in the right direction.

Thanks, 

Chris

---

