---
title: "NVIDA or Ubuntu-nvidia driver"
date: 2007-06-29
forum: Multimedia &amp; Video
---

### Post by GeeZor on 2007-06-29
Hi,

Im working on an 'older' machine (1Ghz) which i stuffed a Nvidia GeForce 5200 FX video card (128Mb) into.
At the moment i am using the video driver provided by Nvidia. Had to build it myself since there is no precompiled driver for Ubuntu 7.04 Feisty Fawn.
Now it came to my understanding that Ubuntu now also supports NVIDIA cards and since i need to recompile the videodriver eachtime i upgrade the kernel i was wondering wheter it would be 'better' to use de distro's driver package. 

However, in reviews i have been reading about the distro supplied driver people are talking about problems with things like resolution-settings and so on.

So basically my question is which will get me better 'THE BEST'  video results? The orignal driver downloaded from NVIDIA or use apt-get to install de driver from de distro's sources' and through that way always be up-to-date.

Thanks in advance.

---

### Post by dabl on 2007-06-29
Regarding Quality Of Display -- there is no difference.  The nvidia-glx-new package has the proprietary -9775 driver built into it. You already have the proprietary driver working, so that's as good as it gets.

Regarding Reliability -- your installation of the proprietary driver will "break" the GUI when a Ubuntu kernel upgrade is installed, and you will have to manually re-install the proprietary driver, from a text-only system.  If you use the packaged driver, it will handle a kernel upgrade without breakage.

---

### Post by GeeZor on 2007-06-29
Thanks Dabl,

Since i doesn't realy make any difference in performance i think i'll stick with the current driver. This way i force myself to keep track of updates regarding the kernel and the kernel sources and headers since i can't install de the proprietary driver without having source and header files for the kernel in place.

Main concern was performance and display qualilty...

again, thanks dabl.

---

