---
title: "two Nvidia cards"
date: 2009-05-12
forum: Multimedia Software
---

### Post by duffrecords on 2009-05-12
I have an Nvidia GeForce 8300 (on-board) and an Nvidia GeForce 9600 GSO (PCI-e).  They were both working at one point.  Then my DVD-RW failed and I had to RMA it.  After removing it, my configuration got messed up and I couldn't seem to reconfigure the 9600, even after the new DVD-RW came.

Both cards are detected by Ubuntu:```
~$ sudo lshw -C display
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: GeForce 8300
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: latency=0
  *-display UNCLAIMED
       description: VGA compatible controller
       product: GeForce 9600 GSO
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
```but if I open System > Administration > Hardware drivers, it recommends the NVIDIA accelerated graphics driver (version 177).  I know, based on NVIDIA's web site and the output of```
sudo apt-cache show nvidia-glx-180
```, that version 180 is the proper driver for both of these cards.  However, if I install either package, the X server will fail to start.  Currently, I can only use the on-board 8300.  What should I try next?

...And not envy; I want to do this by hand so I'll remember it the next time it breaks.

---

### Post by starsheeep on 2009-05-12
You have to do [this]("http://ubuntuforums.org/showthread.php?t=1139101") and select one of your GPU's in xorg.conf

---

### Post by duffrecords on 2009-05-19
I asked for help on nvnews.net and NVIDIA support alerted me to the fact that using multiple graphics cards with newer kernels tends to exhaust the kernel virtual address space.  So I added ```
vmalloc=256MB
```to the kernel parameters in GRUB, which enabled X to start.  However, it froze after I entered my password.  So once I realized the problem was memory-related, I remembered I had tried setting my RAM to 128-bit ganged mode.  Once I reset it to 64-bit unganged, everything started working like a charm.

---

