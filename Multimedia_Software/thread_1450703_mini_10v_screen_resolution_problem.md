---
title: "mini 10v screen resolution problem"
date: 2010-04-09
forum: Multimedia Software
---

### Post by joe7203 on 2010-04-09
I have a Dell mini 10v (Intel GMA950 chipset).  The netbook screen resolution is supposed to be 1024x600, but the only options shown in Ubuntu are 800x600 and 800x576.  I have tried xrandr to create another screen resolution option and always fail on this step...

 ~$ xrandr --output default --mode 1024x600_60.00
xrandr: Configure crtc 0 failed

Although the new resolution shows up in Ubuntu's display manager, it errors with:  "could not set the configuration for CRTC 256"

I have also tried to edit my xorg.conf file, but not really sure how to set it up right.  

I have tried this on both Ubuntu 9.04 & 9.10

thanks!

---

### Post by joe7203 on 2010-04-09
$ sudo lwhw -C display 

  *-display UNCLAIMED     
       description: VGA compatible controller
       product: System Controller Hub (SCH Poulsbo) Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: latency=0


I don't think it should be UNCLAIMED, ideas?

---

