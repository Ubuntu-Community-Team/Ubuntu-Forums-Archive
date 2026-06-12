---
title: "Mythbuntu - PVR USB2 Not working"
date: 2009-01-06
forum: Mythbuntu
---

### Post by ripperzane on 2009-01-06
Hello all. I have a PC running Mythbuntu 8.10, and cant seem to get my PVR-USB2 (from Hauppauge) to work, when it worked fine and the remote did not using 8.04.1. I know the workaround exists for the remote in the previous version (8.04.1) but the issue is that I cannot use the USB device I was just using before... Any assistance or tips/diagnostics would be swell.

I know some about ubuntu, not not a guru, and reaching out for assistance in this matter.
Regards,
Zane


UPDATE: Trying a work around. The usb seems to be glitchy when plugging this device (PVR USB2), so simply doing a server 8.10 x86 install, then going to install mythbuntu desktop (or whatever the corresponding package is named) then goin to do the same for my frontend (Ubuntu 8.10 Desktop using the alternate disk and doing a command line install, then using the same package for frontend.) The front end will be CLi to allow for the kernel to be compatible with the NVidia drivers that will need to be installed. I have read somewhere that server kernels sometimes conflict with newer installs of NVidia proprietary drivers.

Guessing this will be lost to the abyss, but I hope it helps some one


UPDATE: This is a known bug. [Here it is on launchpad.]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/262927")

---

