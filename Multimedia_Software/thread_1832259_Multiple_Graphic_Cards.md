---
title: "Multiple Graphic Cards"
date: 2011-08-24
forum: Multimedia Software
---

### Post by wenkep3 on 2011-08-24
I'm running Ubuntu 10.10 with two graphic cards.  I have two monitors up and running on a nVidia card and am looking to add a third monitor on a Radeon card.  The third monitor appears to be recognized and can play audio, but nothing appears on the screen.  A signal is being sent because the "no signal" message is not displayed.  Does anyone know how to get the third monitor up and running?  Below is my display information.

Thanks,
  Paul

> 
  *-display               
       description: VGA compatible controller
       product: G98 [GeForce 8400 GS]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:fa000000-faffffff memory:c0000000-cfffffff memory:f8000000-f9ffffff ioport:cf00(size=128) memory:fb000000-fb01ffff
  *-display
       description: VGA compatible controller
       product: Radeon RV100 QY [Radeon 7000/VE]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=64 mingnt=8
       resources: irq:21 memory:d8000000-dfffffff ioport:de00(size=256) memory:fdef0000-fdefffff memory:fde00000-fde1ffff


---

