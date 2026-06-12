---
title: "Iwl 4965 and airdriver problems"
date: 2011-06-18
forum: Networking &amp; Wireless
---

### Post by bhawk1987 on 2011-06-18
recently ive had a problem trying to run aireplay-ng on ubuntu, it seems packet injection isnt working (channel is fixed on -1).
So ive researched and downloaded compat wireless and also tried running airdriver to get the driver to work but whenever i run airdriver this is all i get


bhawk@bhawk-VGN-NR21Z-S:~$ sudo airdriver-ng install 14
[sudo] password for bhawk: 
Driver "Intel Pro Wireless 4965 A/B/G/N" specified for installation.
Your current GCC version doesn't match the version your kernel was compiled with.
The build modules will probably not load into the running kernel.
DI_DRIVERPATH1[14] isn't set, you need at least one driver source!
Running "depmod -ae"...
WARNING: -e needs -E or -F
Failed to install the driver.
Look through "/var/log/airdriver" for errors.


Now where do i go from here?
How do i get my wireless card to work with aircrack?

Many thanks in advance

Ben

---

