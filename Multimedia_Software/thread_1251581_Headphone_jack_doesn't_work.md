---
title: "Headphone jack doesn't work"
date: 2009-08-27
forum: Multimedia Software
---

### Post by lateralus01 on 2009-08-27
I'm running Ubuntu 9.04 on a sony vaio FZ-140E laptop.  For some reason my headphone jack doesn't work.  Plugging headphones into it produces no sound on the headphones and doesn't interrupt sound on the speakers built into the laptop.

```

mark@Ubuntu:~$ sudo lshw -C multimedia
  *-multimedia            
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

```

Thats as much information that I know how to get if you need more just ask.

Thanks,
Lateralus01

---

### Post by checarlos87 on 2009-08-28
I have the exact same problem (with the exact same controller) on a VAIO FZ280E.  Help would be greatly appreciated.

---

### Post by juicyoner on 2011-04-01
This thread is from 2009. Someone must have fixed this problem since then, right?

(bump)

---

