---
title: "Multiple video controllers Dell XPS15 L502X"
date: 2011-03-15
forum: Multimedia Software
---

### Post by whitethunder922 on 2011-03-15
I have a Dell XPS15 L502X laptop and I installed 10.10 on it. Basic video works but I'd like to install the better drivers. When I do System > Administration > Additional Drivers, it installs Nvidia driver version 260. When I restart X, it fails to load, saying:

Fatal server error: no screens found

Below are the output of lspci and lshw -C video. It looks like I have 2 video controllers, but which one should I be using for the laptop display? And any idea why the Nvidia one isn't working? Thanks.


lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Sandy Bridge Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: nVidia Corporation Device 0df5 (rev a1)


lshw -C video
  *-display
       description: VGA compatible controller
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:f0000000-f0ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:3000(size=128) memory:f1000000-f107ffff
  *-display
       description: VGA compatible controller
       product: Sandy Bridge Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:48 memory:f1400000-f17fffff memory:e0000000-efffffff ioport:4000(size=64)

---

### Post by bcbc on 2011-03-18
Have a look at this thread: [http://ubuntuforums.org/showthread.php?t=1618801](http://ubuntuforums.org/showthread.php?t=1618801)

It's about the L501X but someone there posted the same error you got. I'm getting an L502X as well so am curious whether you can get the nvidia Optimus card working.

EDIT: just found this one [http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660) ; it warns against installing nvidia drivers. Also shows how to fix it if you have already.

---

### Post by codedivine on 2011-03-27
Sorry to say this, but as the other post points out, if you have an Optimus based laptop, you will likely not be able to use the Nvidia card at all in Linux right now. The only thing you can do is check in the BIOS if it allows you to set it to use discrete graphics all the time.

---

