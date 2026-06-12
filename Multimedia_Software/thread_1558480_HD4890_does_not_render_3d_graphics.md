---
title: "HD4890 does not render 3d graphics"
date: 2010-08-22
forum: Multimedia Software
---

### Post by w1ntermute on 2010-08-22
Hello everyone,

I just installed Ubuntu 10.04 on my machine, and had the intention to also use this pc to play some computer games (like Quake!).

I installed the proprietary FGLRX driver and have noticed an increase in performance when doing very basic tasks with the Gnome environment (Doesn't lag when scrolling, opening menus, etc). However, the card does not seem to want to render 3d graphics. Quake Live simply leaves me with a blank screen, and likewise glxgears just shows a blank window. The drivers do seem to work and are installed, as **sudo lshw -c display** outputs:

```
  *-display               
       description: VGA compatible controller
       product: RV790 [Radeon HD 4800 Series]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:50 memory:d0000000-dfffffff(prefetchable) memory:fe9e0000-fe9effff ioport:d000(size=256) memory:fe9c0000-fe9dffff(prefetchable)

```So clearly the driver is working.

I am not too hot on working with display adapters, and I have not been able to find anybody experiencing the same problem as me.

Any suggestions? All help is appreciated

Thanks.

---

### Post by w1ntermute on 2010-08-24
Going to give this thread one bump, with some extra info.

It seems the glxgears demo renders if it's the first thing I run when entering the X Desktop (I run GNOME), but after running something else like firefox, the demo no longer renders. I've tried running OpenArena as the first application to run at X, but after going to fullscreen nothing renders, and killing the process does not seem to revert my desktop back to its original resolution.

---

