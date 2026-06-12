---
title: "Unichrome Pro K8M800 Lock-ups"
date: 2006-06-15
forum: Multimedia &amp; Video
---

### Post by ahaslam on 2006-06-15
Hi, 

I have a Via Unichrome Pro IGP (k8m800) in a laptop. It was impossible to get this to work on the 'via' driver with dri on in Breezy. Although X.org still say that the K8M800 is unsupported, it works in Dapper out of the box. 'glxinfo' shows that dri is on & 'glxgears' produces 421 fps.

While multimedia is vastly improved, I still can't play any games. Some games such as Quake II run perfectly (in wine) at full resoloution, with high quality textures at a constant 25 fps, but they always crash at random points:(  Even simple games such as Tuxracer crash the system.

I would like to know if there's any alternate (but stable) drivers that anyone has had more luck with, and how to go about installing them. Or if anyone out there has the same K8M800 chipset and has got it working properly (and how).

Thanks in advance,
Tony.

---

### Post by ahaslam on 2006-06-15
Must be a hot topic or a popular chipset - 10 views in 10 hours, one of them being myself.

---

### Post by Tomy on 2006-06-19
[quote=Anthony Haslam]Hi, 
I have a Via Unichrome Pro IGP (k8m800) in a laptop. It was impossible to get this to work on the 'via' driver with dri on in Breezy. Although X.org still say that the K8M800 is unsupported, it works in Dapper out of the box. 'glxinfo' shows that dri is on & 'glxgears' produces 421 fps.
 
While multimedia is vastly improved, I still can't play any games. Some games such as Quake II run perfectly (in wine) at full resoloution, with high quality textures at a constant 25 fps, but they always crash at random points:(  Even simple games such as Tuxracer crash the system.
 
I would like to know if there's any alternate (but stable) drivers that anyone has had more luck with, and how to go about installing them. Or if anyone out there has the same K8M800 chipset and has got it working properly (and how).
 
 Thanks in advance,
 Tony.[/quote]  
 
I have the same K8M800 Unichrome Pro chip on a MSI motherboard and have the same problems. There is a bug that was reported back in November 2005 that apparently still is unfixed.
 
 [https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-via/+bug/43154]("https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-via/+bug/43154")
 
 Some have been able to compile the "openchrome" driver from here:
 
 [www.openchrome.org]("http://www.openchrome.org")
 
 but when I tried I failed ](*,)
 
I use Dapper Drake but can not play tuxracer (aka planetpenguin) and have to disable screensavers or else my computer freezes solid.
 
 Hopefully someone will fix this RSN. It is unfortunate that critical bugs go unfixed for such a long period of time. 
 
I love Free software but sometimes I wish there was a more direct way of paying money to get something fixed. I would be willing to pay at least 5 times the cost of the motherboard ( a mere $62 ) to get this bug fixed. Unfortunately there is no way to pay and no one to pay and it appears to me that the good people over at x.org are not interested in making the "via" driver work for the Unichrome Pro IGP. 
 
The "via" driver does work fairly well for the Unichrome IGP but I think people lost interest and motivation to fix the bugs with the Unichrome Pro.
 
 Tomy

---

### Post by ahaslam on 2006-06-24
Thank you for your reply.
I also had no luck with the openchrome drivers, just got a frosted screen. I read that more luck is obtained while using a CRT with the openchrome driver. 
I really hope that these bugs are ironed out in the 'via' driver. It is the only gripe that I've got with Linux, as it's making an otherwise stable OS unstable.
Thanks again,
Tony.

---

