---
title: "trying to create 3 monitor setup"
date: 2011-03-10
forum: Multimedia Software
---

### Post by veilig on 2011-03-10
I'm trying to create a 3-monitor setup, where I can move windows between all three monitors.  I currently have two monitors on one video card.  I was recently given another video card to add the third.  It feel like I should be able to get this to work, but am looking for good advice before I start.  I currently have both cards installed and can view the startup screen on the 3rd monitor out of the box (the ubuntu w/ 6 dots underneath it).  But, thats all I can see.  whats weird is when I reboot, then I can't see that screen anymore.  the monitor just goes black.

Here is some info on my cards

```
sudo lshw -C video  
  *-display               
       description: VGA compatible controller
       product: RV620 LE [Radeon HD 3450]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:45 memory:a0000000-afffffff memory:fbdf0000-fbdfffff ioport:c000(size=256) memory:fbdc0000-fbddffff
  *-display
       description: VGA compatible controller
       product: NV44A [GeForce 6200]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=64 maxlatency=1 mingnt=5
       resources: irq:21 memory:fd000000-fdffffff memory:c0000000-dfffffff memory:fc000000-fcffffff memory:febe0000-febfffff

```


```
lspci | grep VGA 
20:01:00.0 VGA compatible controller: ATI Technologies Inc RV620 LE [Radeon HD 3450]
25:05:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

```

---

