---
title: "No Sound in Ubuntu Studio 11.10"
date: 2011-11-10
forum: Multimedia Software
---

### Post by Yosefu on 2011-11-10
Hi, I hope this question is in the right place!

After installing Ubuntu Studio 11.10 sound worked properly. I tweaked some stuff to get Jack, Zynaddsubfx and mi midi controller working as well, but I might have screwed it all up. Maybe it was something else.

Now "aplay -l detetcs" no soundcard.
however, "sudo lshw -C multimedia" gives me this:
 *-multimedia UNCLAIMED  
       description: Audio device
       product: Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: latency=0
       resources: memory:b4020000-b4023fff
  *-multimedia UNCLAIMED
       description: Audio device
       product: 5 Series/3400 Series Chipset High Definition Audio
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 05
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:b4100000-b4103fff

I've also tried an alsa update script which hasn't worked for me. 
I'm a total noob in linux, I don't know how to proceed here...

Thanks!

---

