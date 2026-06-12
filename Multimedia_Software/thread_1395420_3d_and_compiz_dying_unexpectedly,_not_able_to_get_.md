---
title: "3d and compiz dying unexpectedly, not able to get it back."
date: 2010-01-31
forum: Multimedia Software
---

### Post by jdrake_nd on 2010-01-31
installed ubuntu 9.10 on a new machine, all by itself, everything worked great, I am using my onboard intel graphics card, after installing x-plane web demo, and running it repeatedly with no ill-effect, I suddenly was kicked back to login screen and when I logged back in, i can no longer get any 3d games or compiz to work at all, I have tried reinstalling all glx-related packages, to no avail.  any ideas would be appriciated.  all 3d games give similar output to:

me@computer:~$ blender
Compiled with Python version 2.6.4.
Checking for installed Python... got it!
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  29
  Current serial number in output stream:  29

my displays are:  (only one monitor hooked up)

me@computer:~$ sudo lshw -C display
  *-display:0             
       description: VGA compatible controller
       product: 82G33/G31 Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:29 memory:fdf00000-fdf7ffff ioport:ff00(size=8) memory:d0000000-dfffffff(prefetchable) memory:fd500000-fd5fffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: 82G33/G31 Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:fde80000-fdefffff


thank you, this has me baffled, since all I did was run a 3d game, and was left with no desktop effects or any other 3d apps.  obviously my trouble is in glx, but where, and how does one go about repairing it?

thanks again,

Justin

---

### Post by jdrake_nd on 2010-02-01
[http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-xorg-without-reinstalling-ubuntu.html](http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-xorg-without-reinstalling-ubuntu.html)

that just had me go through and reinstall xorg, after that, it all works fine... the question would be why did it die, and how to prevent from having to do that again in the future...

---

