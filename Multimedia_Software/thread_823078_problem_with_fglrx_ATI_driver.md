---
title: "problem with fglrx ATI driver"
date: 2008-06-08
forum: Multimedia Software
---

### Post by vmatikov on 2008-06-08
I have a problem on my Myth box when I installed the ATI fglrx driver. I installed the driver from the Catalyst driver on AMD/ATI's website. After I installed and added appropriate lines to  my xorg.conf file, I rebooted my machine. On the first reboot, everything is fine. I can run the fglrxinfo command and see that the ATI driver is in use. After the second, and all subsequent at that, reboot, X crashes and loads Ubuntu in low-res mode. I checked the X log file and found that after the second reboot, instead of loading with the xorg.conf, X loads with xorg.conf.failsafe. I have tried both the ATI Ubuntu driver (pre-compiled, via Hardware Drivers manager) as well, there the driver does not load period. My equipment is:

CPU: AMD Athlon 64 X2 4400+ 
MOBO: GIGABYTE GA-MA69GM-S2H
VIDEO: ATI RADEON XPRESS 1250 (ONBOARD)

---

