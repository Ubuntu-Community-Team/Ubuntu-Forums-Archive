---
title: "Poor screen resolution on Lucid+Fluxbox+aterm"
date: 2011-10-02
forum: Multimedia Software
---

### Post by neela on 2011-10-02
I just installed a minimal version of Ubuntu 10.04 server, and added Fluixbox and aterm to it. The font in the aterm is really poor -- I suspect because I do not have the right graphic drivers. The machine is a Dell Vostro 200 with Intel 82G33/G31 integrated graphics. I previously ran Gnome, and I suspect I picked up the nvidia driver which looked pretty good. Had to dump these because someone broke into my system. Wondering how I can get back nvidia -- just for the clean fonts -- not for 3D etc. would appreciate any help.

Thanks
Neela

---

### Post by matt_symes on 2011-10-03
Hi

Lets get some basic information about your system. Open a terminal and type these commands. Post the results back here.

```
sudo lshw -c video
xrandr
```

Kind regards

---

### Post by neela on 2011-10-03
*-display
     description: VGA compatible controller
     product: 82G33/G31 Express Integrated Graphics Controller
     vendor: Intel Corporation
     physical id: 2
     bus info: pci@0000:00:02.0
     version: 02
     width: 32 bits
     clock: 33MHz
     capabilities: msi pm bus master cap list rom
     configuration: driver=i915 latency=0
     resources: irq:26 memory:fdf00000-fdf7ffff ioport:ff00(size=8) memory:d0000000-dfffffff(prefetchable) memory:fdb00000-fdbfffff




Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 4096 x 4096
VGA1 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 474mm x 296mm
   1680x1050     60.0*+
   1600x1200     60.0
   1400x1050     60.0
   1280x1024     75.0
   1440x900      750.0  59.9

etc..  I was hand typing these things..

---

### Post by matt_symes on 2011-10-04
Hi

> **neela said:**
> *-display
     description: VGA compatible controller
     product: [COLOR=Red]82G33/G31 Express Integrated Graphics Controller[/COLOR]
     vendor: Intel Corporation
     physical id: 2
     bus info: pci@0000:00:02.0
     version: 02
     width: 32 bits
     clock: 33MHz
     capabilities: msi pm bus master cap list rom
     configuration: [COLOR=Red]driver=i915[/COLOR] latency=0
     resources: irq:26 memory:fdf00000-fdf7ffff ioport:ff00(size=8) memory:d0000000-dfffffff(prefetchable) memory:fdb00000-fdbfffff

Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 4096 x 4096
VGA1 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 474mm x 296mm
   [COLOR=Red]1680x1050     60.0*+[/COLOR]
   1600x1200     60.0
   1400x1050     60.0
   1280x1024     75.0
   1440x900      750.0  59.9

etc..  I was hand typing these things..

You have a driver installed for your card and you have a number of resolution you can choose from.

Some questions....

1. Is it only the font that are giving you problems ?
2. What fonts do you have installed currently ?
3. Can you post a screen shot showing the problem fonts as you see them ?

Kind regards

---

