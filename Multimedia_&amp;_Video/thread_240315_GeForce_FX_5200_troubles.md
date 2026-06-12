---
title: "GeForce FX 5200 troubles"
date: 2006-08-20
forum: Multimedia &amp; Video
---

### Post by IAmNotPhillip on 2006-08-20
I am currently having problems getting Dapper to work with my GeForce FX 5200 PCI card. It works perfectly with the onboard intel gfx, but as you probably know, onboard cards generally suck. ;)

I have added my GeForce to the xorg.conf file and switched it to default, but then Ubuntu always hangs when it's loading hardware drivers. I already have the latest nvidia drivers installed, so I can't really think of what could be the problem. (note: I have tried both 'nv' and 'nvidia' as the driver -- neither worked)

A forum/guide/wiki search as also proved fruitless, as most of them are for already working cards that wish to add 3d acceleration.

Is there a guide or something that show's step-by-step the proper way to switch from integrated graphics to a PCI card? I'm 90% sure the problem is user error, but I can't find it.  >.<

---

### Post by tseliot on 2006-08-20
Try this guide:
[http://doc.gwos.org/index.php/Nvidia_Intel_Integrated](http://doc.gwos.org/index.php/Nvidia_Intel_Integrated)

---

### Post by IAmNotPhillip on 2006-08-20
Thank you, thank you, thank you! It worked wonderfully!
:D

---

