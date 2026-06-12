---
title: "SoundMax on Ubuntu 6.10 inVMWare"
date: 2007-03-24
forum: Multimedia &amp; Video
---

### Post by RealTonko on 2007-03-24
I am running Ubuntu 6.10 inside VMWare Server 1.0.1 build-29996 running under Windows XP SP2 on Dell Dimension 8400.

XP system has Analog Devices SoundMax Integrated Audio. So I tried building and installing Analog Devices ALSA drivers from [http://www.alsa-project.org/](http://www.alsa-project.org/). With no success. 

Then lspci output revealed that VMWare virtualized multimedia driver is Ensoniq ens1371, even if you add it via VMWare Server Console as SoundMax audio driver.

Building and installing ens1371 driver was painless, following alsa instructions. It required a reboot and editing /etc/modules.conf to actually hear the sound (i.e. injecting kernel modules after the install was not enough).

Hope this helps someone who's crazy enough to attempt configuring a fully functional Ubuntu inside VM on XP.

---

