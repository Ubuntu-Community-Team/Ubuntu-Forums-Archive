---
title: "Installed Nvidia drivers, enable twinview, reboot, and can't boot"
date: 2010-10-12
forum: Multimedia Software
---

### Post by at165db on 2010-10-12
I have a GeForce 9500 GT, which worked great with 9.10.
I did a fresh install of 10.10.

Before I installed the nvidia drivers, both monitors came up, in clone mode just fine, but I don't want clone mode.  I installed the nvidia drivers via the "Additional Drivers" application, chose the current nvidia ones.  A reboot later and I notice the different boot up screen which is a known issue that I don't care about.

Here is where things go awry:
If I ```
sudo nvidia-settings
``` I can configure my twinview as I had it in 9.10.  I can apply it, and it works.  I can't save the xorg config.  Next time I reboot, my desktop hangs before the blue kubuntu 10.10 screen would appear.  All I see is a black screen with a blinking ```
_
```, the box never boots, I can't ssh to it or pull up the ttys with ctrl+alt F1-F6.

If I reboot the computer (via power switch) it will boot back up, but the 2nd monitor is disabled, and I have to re-config the displays with nvidia-settings.

Is anyone else having this issue?  Is it possible to safely persist nvidia-settings?  How can I find out more about the failure to boot so I can get to the bottom of this?

Thanks,
Russell

---

