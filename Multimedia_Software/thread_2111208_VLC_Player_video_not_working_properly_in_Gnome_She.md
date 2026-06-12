---
title: "VLC Player video not working properly in Gnome Shell Classic"
date: 2013-02-01
forum: Multimedia Software
---

### Post by C.Clear on 2013-02-01
Alright So I recently updated to 12.04 and installed Gnome shell for the classic look of Ubuntu which I prefer to Unity.

Whenever I play a file in VLC Player it plays well for a while and seems to play great whenever I start the computer. However after a while the screen goes black.

On my first update to 12.04 in the Unity Environment, the problem was worse. I had absolutely no video in either Gnome Media Player or VLC Has anyone else encountered this problem or a variation on it? and if so any recommendations ?

---

### Post by C.Clear on 2013-02-05
Alright. Been investigating the problem and it looks like my drivers got messed up on upgrading to ubuntu 21.04 Not quite sure what is the dpkg command for reinstalling video drivers.  Just in case I'm missing something going to post the lshw result. Doubt its the video card. cause videos work fine in Windows on the sampe computer 

```
 
**sudo lshw -c video  **
 *-display               
       description: VGA compatible controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:e8000000-efffffff memory:feb80000-febfffff



```

---

