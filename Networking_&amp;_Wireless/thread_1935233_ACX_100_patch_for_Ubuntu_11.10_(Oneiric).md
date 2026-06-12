---
title: "ACX 100 patch for Ubuntu 11.10 (Oneiric)?"
date: 2012-03-03
forum: Networking &amp; Wireless
---

### Post by RHub787 on 2012-03-03
Just got my fresh install of Ubuntu 11.10 (Oneiric) using a bootable USB and NO driver for my wireless card. which has the Texas instruments ACX 100 chipset.

I did find this thread: "**How to compile acx 100/111 driver in Karmic**" ([http://ubuntuforums.org/showthread.php?t=1321303](http://ubuntuforums.org/showthread.php?t=1321303))

However this patch is for KARMIC. and did not work for me.  

Was wondering if there is some way to modify it for ONEIRIC.  Or if there is another method i could try.

_________________________________

Ubuntu 11.10 Onerirc
XP Dual boot seperate partition

---

### Post by ockac23 on 2012-05-25
[http://sourceforge.net/apps/mediawiki/acx100/index.php?title=ACX100](http://sourceforge.net/apps/mediawiki/acx100/index.php?title=ACX100)

but it seems not to work with Oneiric.
I have the same problem. I have Ubuntu 11.10 (Oneiric) with 3.0.0-20-generic. 
I am trying to "liven up" a USB wireless D-link DWL 120+ which has ACX100 chipset.

It doesn't work. Maybe I am doing something wrong.

Development stopped in early 2008, it seems, when the ACX module was incorporated in the mainline kernel. Now, it seems it's an orphan.

Can anyone help us with this?

---

### Post by ockac23 on 2012-05-28
So there is no chance, isn't it guys? :-(

---

### Post by mringer on 2012-05-30
Warning: I know nothing about this device. Have you 
tried

[http://acx100.sourceforge.net/](http://acx100.sourceforge.net/)

---

### Post by ockac23 on 2012-05-30
> **mringer said:**
> Warning: I know nothing about this device. Have you 
tried

[http://acx100.sourceforge.net/](http://acx100.sourceforge.net/)

Yes I have tried it. Did not work. Seems to be an old project abandoned 2008 (i guess). Maybe works with old kernel versions...

---

### Post by mringer on 2012-06-17
> **ockac23 said:**
> Yes I have tried it. Did not work.... 

All I can suggest is ndiswrapper (worked for me on completely 
different hardware). If you want to try this, you need the Guide
(sticky on this Forum). I regret that I cannot help any farther.

---

### Post by O2Blevel on 2012-06-17
I downloaded the driver from this link:

[git clone git://acx100.git.sourceforge.net/gitroot/acx100/acx-mac80211]("git clone git://acx100.git.sourceforge.net/gitroot/acx100/acx-mac80211")

cd into directory, make, sudo make install, depmod, to set it up. Check the included readme first. It installs as a kernel module so any kernel update will require a reinstall....takes just a few minutes.

---

