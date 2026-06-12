---
title: "nvidia driver problems, no restricted devices entry"
date: 2007-06-18
forum: Multimedia &amp; Video
---

### Post by abierbaum on 2007-06-18
Hello all,

I am trying to get the nvidia binary driver working on ubuntu 7.04.  I have used this driver for quite a while with other version of Linux, but I can't seem to get this working with ubuntu.

I have a Dell Latitude D820 (x86_64) with a  GeForce Go 7400 chip.

I am tried two methods:

- First I tried to follow the recommended instructions on the wiki 
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29)

This seems to fail immediately because the restricted device manager does not list anything for the nvidia board.  It only has a single entry for the intel wireless 3945 in the machine.  I made sure that the correct linux-restricted package is installed (linux-restricted-modules-2.6.20-16-generic).  There are "nvidia","nvidia_legacy", and "nvidia_new" directories under /usr/lib/linux-restricted-modules/2.6.20-16-generic and there are object files in those directories (ex: nvidia_new contains: "nv-i2c.o  nv-kernel.o  nv-vm.o  nv.o  nvidia.mod.o  os-agp.o  os-interface.o  os-registry.o")

So my question is, what am i doing wrong.  What do I have to do to get nvidia to show up in the restricted manager.

- The second method I tried was just to install the nvidia packages directly (nvidia-glx-new).

This seems to have installed the driver, but the kernel module does not appear to get loaded.  

is there something else I have to do beyond installing the package and enabling the "nvidia" driver in the xorg.conf file?

Thanks,
Allen

---

### Post by abierbaum on 2007-06-20
For those of you keeping track at home, I have found a solution.

i ended up using the envy installer (see other posts in this forum for details).  it still seems like a bit of a hack, but things are working now that that is the important part.  Hopefully I didn't mess up my configuration by not using the recommended method of installing the driver. :(

---

### Post by dabl on 2007-06-20
Envy is a perfectly reasonable way to install the proprietary driver.  Just as when you use the Nvidia downloaded installer, a Linux kernel upgrade will disable your driver when you're not using the package (nvidia-glx-new).  So, if/when that happens, in the text console type ```
sudo envy -t
``` and you'll soon be back in business.

If you want to let the Nvidia driver set you up for compositing and glx, you will need to type (in a console window) ```
sudo nvidia-xconfig --add-argb-glx-visuals --composite
```

Likewise, if you want to change the default resolution and refresh rates, and let your graphics card auto-detect the monitor, bring up the driver utility with ```
sudo nvidia-settings
``` choose "X Server Configuration", then autodetect the monitor, choose your resolution and refresh rates, and then hit the "Save To X Configuration File" button in the lower right, and click "save" when the little window pops up.  You only need to do this once -- for subsequent visits to the driver utility, you don' t need to be the Super User so you can just enter ```
nvidia-settings
``` in a console window.

:)

---

