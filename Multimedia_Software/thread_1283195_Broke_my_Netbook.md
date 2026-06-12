---
title: "Broke my Netbook"
date: 2009-10-05
forum: Multimedia Software
---

### Post by jjachnik on 2009-10-05
So while trying to improve the intel graphics on my netbook (UNR 9.04), I found this link [http://www.h-online.com/open/Updated-graphics-drivers-for-Ubuntu-9-04--/news/113261]("http://www.h-online.com/open/Updated-graphics-drivers-for-Ubuntu-9-04--/news/113261")

I added the xorg-edgers repository then did an upgrade which installed update xorg drivers. Now my netbook is almost unusable it is so slow. How can I revert to the old driver?

If i remove the xorg-edgers repository and then completely remove the xorg intel drivers via synaptic, i guess it will be forced to get new drivers from the normal repositories containing the old driver. Will this work or will completely removing the graphics driver destroy my system?

---

### Post by DJonsson2008 on 2009-10-05
Sounds like you will need to edit our xorg.conf,
perhaps even using the generic vesa drivers 
until you get the other drivers sorted out.

Search ubuntu forums for "xorg.conf"
or "edit xorg.conf", there should be
plenty of info.

---

### Post by jjachnik on 2009-10-05
How do you delete threads?

I just solved my problem. In Synaptic you can do 'Force Version' so i downgraded to the old driver. It is fine now.

---

### Post by DJonsson2008 on 2009-10-05
To be a little clearer, it might be a good
idea to get your machine working with the
vesa generic drivers. You can do that via
editing your xorg.conf file. Then backup
your xorg.conf file as xorg.conf.vesa.works.bak
or something like that. Once you have that 
routine down you can roll back if your
driver install upgrade does not pan out,
so at least you can get your work done.

---

### Post by jjachnik on 2009-10-05
just tried the vesa driver but it was really slow. Back to the old one. It's not too bad, the main problems are flash videos and if i turn on visual effects the display screws up. Apparently they will fix it in 9.10 anyway. Just have to wait and hope.

---

### Post by pmlxuser on 2009-10-05
> **jjachnik said:**
> How do you delete threads?

I just solved my problem. In Synaptic you can do 'Force Version' so i downgraded to the old driver. It is fine now.


Hey when we find a solution to a problem we don't delete the thread we just mark it solved...

---

