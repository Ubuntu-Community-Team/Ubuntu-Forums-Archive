---
title: "3D acceleration broke"
date: 2006-06-23
forum: Multimedia &amp; Video
---

### Post by elispiro on 2006-06-23
Hi all! Upon installation of Ubuntu, 3D worked fine on my Radeon 9600SE. I decided to try the fglrx driver, so I followed all the instructions on the Ubuntu binary driver howto. Unfortunately, 3D doesn't work anymore, whether I use the stock "ati" driver or fglrx. Is there any way to reset my xorg.conf or something like that to go back to the way it was before? I don't need fglrx, but I want 3D to work.

---

### Post by gborzi on 2006-06-23
Your xorg.conf should have the > Load "dri" entry in the Module Section, and you need to have libgl1-mesa-dri installed.

---

### Post by elispiro on 2006-06-23
Load dri is there, and libgl1-mesa-dri is already installed...

---

### Post by gborzi on 2006-06-23
Have you tried the radeon driver in xorg.conf instead of the standard ati ? I use this driver for my Radeon 7500M, and I don't have any problem with dri.

---

### Post by elispiro on 2006-06-23
What driver is that? Is it just "radeon"?

---

### Post by gborzi on 2006-06-23
Yes, it's radeon instead of ati. My xorg.conf device section looks like this:
> 
Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
        Driver  "radeon"
        BusID           "PCI:1:0:0"
        Option  "RenderAccel"   "yes"
EndSection

I have other options in the section that are specific for my card. I can attach my xorg.conf file if you would like to see it.

---

