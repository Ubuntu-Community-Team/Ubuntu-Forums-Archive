---
title: "Installed Nvidia drivers, now X does not work"
date: 2007-10-04
forum: Multimedia &amp; Video
---

### Post by phargarten on 2007-10-04
I just installed the newest Nvidia drivers for whatever reason (are the ones installable from the default GUI good enough) and now X is broken. Ubuntu starts into a command line interface.

I can go back into xorg.conf and change the driver back to nv but when I try to run the install under restricted drivers it reverts back to my install. How can I remove any effect of the driver install and just use the provided driver?

Thanks

---

### Post by distroman on 2007-10-04
What kind of grafik card do you have?
How did you install the driver from the nvidia site?

If the driver from the Restricted Drivers Manager works then I see no reason not to use it.

---

### Post by phargarten on 2007-10-04
HP dv2000t laptop
Centrino Duo
GeForce Go 7200 Pci-e


I downloaded the 100.14.19 driver. Shutdown Xserver and ran the install. The install compiled something and ran, but on reboot the driver was crashing. It left me in command line. 

I could go into xorg.conf and revert back to the "nv" driver but now when using the restricted drivers install it seems to take me back to the crash.

I ran the following s/in attempt to remove the new driver:

sudo apt-get remove --purge nvidia-glx-new
sudo rm /lib/linux-restricted-modules/.nvidia.new.installed

I also changed the folders in /lib/linux-restricted-modules/2.6*/(nvidia, nvidia_new, nvidia_legacy) all to nvidia_*-old but still no luck. 

The restricted drivers were working f or me and would allow for compiz/beryl but I dont know what to do next.

Please HELP ME! haha.

---

### Post by distroman on 2007-10-04
> sudo apt-get remove --purge nvidia-glx-new
I think this one would remove the driver installed with Restricted Drivers Manager. 

> sudo rm /lib/linux-restricted-modules/.nvidia.new.installed
I also changed the folders in /lib/linux-restricted-modules/2.6*/(nvidia, nvidia_new, nvidia_legacy) all to nvidia_*-old but still no luck.
I think that would be a workaround ala this one.
[http://www.robdian.co.uk/content/view/56/](http://www.robdian.co.uk/content/view/56/)

Anyway you can try to remove the driver from the nvidia site with --uninstall

```
NVIDIA-Linux-*-pkg1.run --uninstall
```

Then give the Restricted Drivers Manager a go agian, lets see what happens. ;-) gl

---

