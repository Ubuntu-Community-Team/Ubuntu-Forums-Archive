---
title: "DVB Drivers dissapearing"
date: 2012-11-29
forum: Mythbuntu
---

### Post by Sctmon on 2012-11-29
Having just enough Linux knowlege to almost keep my mythtv system running I could use some advice!

In order to use my TerraTec Cinergy T Pcie Dual tuner card I had to build and install the V4L-DVB drivers. Helpful guide [here]("http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers").

Every now and then after installing system updates the drivers dissapear along with the dvb folder and any refrence to the tuners in mythtv-setup and I need to rebuild the drivers and fix the myth setup.

Can this be avoided and still keep the system up to date? I assume it is to do with new kernals being installed.

---

### Post by klc5555 on 2012-11-29
That's the price of using home-compiled kernel drivers not included in the generic kernel tree. Since kernel modules are specific to the running kernel they're compiled on, every time the kernel is upgraded, any home-compiled drivers need to be recompiled and reinstalled.

It can't be avoided, but it can be managed. For example, you can do updates (and the recompile if the kernel is upgraded) at times you choose, when there are no recordings scheduled for a while, rather than updating automatically.

---

### Post by Sctmon on 2012-11-29
Thanks for the info, I will just keep re compiling until kernel 3.3..x.x when my tuner card will be supported!

---

### Post by klc5555 on 2012-11-29
Ubuntu kernel packages for kernel 3.5.0 exist for Ubuntu 12.04 updates and 12.10. Upgrading kernels in Ubuntu is much less pleasant than in many (most?) distros, but if you wished to begin to research the topic, a reasonable starting point might be [http://www.howopensource.com/2012/07/how-to-install-linux-kernel-3-5-quantal-in-ubuntu-12-04-11-10-11-04-10-10-and-10-04/](http://www.howopensource.com/2012/07/how-to-install-linux-kernel-3-5-quantal-in-ubuntu-12-04-11-10-11-04-10-10-and-10-04/)

---

### Post by nickrout on 2012-11-29
> **Sctmon said:**
> Thanks for the info, I will just keep re compiling until kernel 3.3..x.x when my tuner card will be supported!Or more easily, stop updating your kernel!

---

