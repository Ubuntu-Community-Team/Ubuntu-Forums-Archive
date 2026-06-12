---
title: "Problems installing Nvidia driver (2.6.19 kernel)"
date: 2007-01-23
forum: Multimedia &amp; Video
---

### Post by eztoril on 2007-01-23
Hi all,

I have problems in getting my Nvidia driver installation to work. I followed successfully a 'HowTo' regarding Nvidia driver installation that I found, but when changing the "Driver" section in the 'xorg.conf' file from my current "vesa" entry to an entry continaing "nvidia" instead, the bootup hangs right before the X-Windows system should start. When changing back the entry to "vesa" again, the bootup works fine. Apparently, the driver isn't correctly installed.

However I found another "HowTo" in this forum, that mentioned three methods doing the Nvidia driver installation. This "HowTo" states (for users that have updated their kernel) that they should install the "restricted-modules" for their current kernel (I began having the Edgy 2.6.17.10 kernel, but have changed it to 2.6.19 kernel).

So, my problem is to find the "restricted-modules" for my new 2.6.19 kernel! Both Synaptic and Adept is listing "restricted-modules" for my old 2.6.17.10 kernel even though I have changes all "edgy" entries in the sources.list file to "feisty"!

Does anyone know where/how to find the restricted-modules -generic for my new 2.6.19 kernel?

Thanks in advance!

Best regards,
Martin

---

### Post by clown99 on 2007-01-23
Try this one, very good stuff

[http://easyubuntu.freecontrib.org/get.html](http://easyubuntu.freecontrib.org/get.html)

uninstall your nvidia-gxl-legacy with synaptic or whatever you have installed, then install with that little helper the new nvidia-driver.

After that do this one

sudo nvidia-xconfig

restart with ctrl+alt+backshift

and it has to be done, so, good fun with :)

---

