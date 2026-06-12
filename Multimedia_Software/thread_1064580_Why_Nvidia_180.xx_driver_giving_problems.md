---
title: "Why Nvidia 180.xx driver giving problems?"
date: 2009-02-09
forum: Multimedia Software
---

### Post by madu on 2009-02-09
Hi,

I cannot seem to get the Nvidia 180.xx driver working in Ubuntu 8.10. As soon as I install the system goes to low-graphics mode with my screen even shifted horizontally. Installing 177.xx back resolves everything.

I have seen many installing 180.xx and with good comments, but I cannot understand why its not working even when the driver is out of beta and officially released by Nvidia (180.22).

I stop the gdm before installing 180.22 but didnt uninstall any previous driver. The installation seems to uninstall them automatically. The second time,  went to Synaptic and removed 'all' Nvidia related drivers. That time I had some errors during 180.xx installation saying some files are missing.

Anybody have any suggestions?

Cheers.

---

### Post by sofasurfer on 2009-02-09
I am correcting this post that I made a few minutes ago. I had posted my solution but I had it wrong because it has been a while since I successfully installed 180. I just found my notes and here is how I did it.

1) install nvidia-glx-180-kernel-source, install nvidia-glx-180-dev, install nvidia-glx-180-modaliases - from synaptic
2) reboot
3) go to system>administration>hardware-drivers and you should see nvidia-180
4) activate nvidia-180
5) reboot
6) verify proper install by going to desktop>change-desktop-background>visual-effects and activate "extra" effects.

---

### Post by madu on 2009-02-09
Thanks mate.
Actually my extra display settings are working perfectly with 177.xx driver which is enabled by default upon the install. Compiz is also working. 

I will try installing from terminal. Before I downloaded the driver from Nvidia and ran in the terminal. Which installed fine without giving any 'explicit' problems. Anyway I will try terminal since maybe there are dependencies.

Thanks man.

---

