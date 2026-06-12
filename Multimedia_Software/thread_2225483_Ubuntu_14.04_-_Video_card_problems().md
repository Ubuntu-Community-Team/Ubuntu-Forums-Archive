---
title: "Ubuntu 14.04 - Video card problems(?)"
date: 2014-05-21
forum: Multimedia Software
---

### Post by toylas on 2014-05-21
I am not sure how to describe this particular problem. Please see the attached images. I have this problem on two machines, one running Ubuntu Gnome 14.04 and the other running Ubuntu 14.04. If I use openbox or pekwm as window managers, the screen does not clear. My guess is that it is some video card problem. Any pointers to the correct problem description and/or solution would be very helpful.

Thanks!

---

### Post by dannyboy79 on 2014-05-21
what graphics card and what drivers? can you post your Xorg.0.log file to pastebin and post the link here so I can see it

---

### Post by toylas on 2014-05-21
Hi dannyboy79, here is the pastebin of Xorg.0.log
[http://pastebin.com/embed_js.php?i=CkYGuS01](http://pastebin.com/embed_js.php?i=CkYGuS01)

Thanks!

---

### Post by dannyboy79 on 2014-05-21
what graphics card?
```
lshw -C Display
```

what graphics driver are you using?
```
lspci -v | grep "Kernel driver in use"
```

---

### Post by toylas on 2014-05-22
Hi dannyboy79,

here is the output of the commands on my HP Touchsmart TM2

> lspci -v |grep 'Kernel driver in use"
        Kernel driver in use: agpgart-intel
        Kernel driver in use: pcieport
        Kernel driver in use: i915
        Kernel driver in use: mei_me
        Kernel driver in use: ehci-pci
        Kernel driver in use: snd_hda_intel
        Kernel driver in use: pcieport
        Kernel driver in use: pcieport
        Kernel driver in use: ehci-pci
        Kernel driver in use: lpc_ich
        Kernel driver in use: ahci
        Kernel driver in use: intel ips
        Kernel driver in use: radeon
        Kernel driver in use: snd_hda_intel
        Kernel driver in use: r8169
        Kernel driver in use: rt2800pci

> lshw -C Display

  *-display
       description: VGA compatible controller
       product: Park [Mobility Radeon HD 5430/5450/5470]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:46 memory:a0000000-afffffff memory:c4400000-c441ffff ioport:3000(size=256) memory:c4440000-c445ffff
  *-display
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:4050(size=8)

Looks like this one has both a radeon graphics card as well as an intel card. Could this be a clash between the two cards? If yes, how would I disable one or the other?

---

