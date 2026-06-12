---
title: "driver for a diamond stealth ati radeon 9250"
date: 2009-01-17
forum: Multimedia Software
---

### Post by moongodjon on 2009-01-17
i have reacently installed a diamond stealth ati radeon 9250 graphics card and it forces me to run in low graphics mode. does anyone know where i could find a driver for such a card and how i would install it? 

ubuntu version:8.04

---

### Post by moongodjon on 2009-01-18
Update: now useing " Radeon " driver but visual effects don't work.

---

### Post by RomeReactor on 2009-01-18
Hi. Have you tried using the ATI driver from 'System->Administration->Hardware Drivers'? If you can't find it there, install the **fglrx-modaliases** package; look for it in Synaptic, or [click here]("apt:fglrx-modaliases") to install it..

---

### Post by moongodjon on 2009-01-19
A) Hardware drivers shows no drivers.

B) fglrx-modaliases does not exist. what repository is it from?

---

### Post by RomeReactor on 2009-01-19
> **moongodjon said:**
> A) Hardware drivers shows no drivers.

B) fglrx-modaliases does not exist. what repository is it from?

It's in "restricted", though it's not available in versions prior to Intrepid. Enable the restricted repository if you haven't already and try installing [xorg-driver-fglrx]("apt:xorg-driver-fglrx"); you may need the [Catalyst Control Center]("apt:fglrx-amdcccle") as well.

Which version of Ubuntu are you running?

---

### Post by moongodjon on 2009-01-19
already installed, and restricted is activated

Ubuntu: version 8.04

---

### Post by RomeReactor on 2009-01-19
As I'm not familiar with ATI cards yet, I hadn't noticed that it looks like [the fglrx driver]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") doesn't support cards earlier than the 9500. [This other page]("https://help.ubuntu.com/community/RadeonDriver") describes the installation and usage of the Radeon driver.

Hopefully someone will be able to provide you with a better answer.

---

### Post by Blue Beard on 2009-01-27
Feature list at [http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature)

Note: Kernel mode settings still a work in progress.

I have great results with my HD3450 and two monitors provided I set BusID and  Driver "radeon" or "radeonhd" after I get the system started with a low level driver.

---

### Post by davidc_0878 on 2010-03-29
Hi,

I know that ATI has the Diamond Radeon 9250 drivers available, but I do not know how to install it. I am still very very new with Linux but the instructions posted with the drivers did not work for me. And I am suspecting that it might be the cause why my Mythbuntu 10.04 Front-end stopped working, so be careful when you try to installing it.

Dave

---

