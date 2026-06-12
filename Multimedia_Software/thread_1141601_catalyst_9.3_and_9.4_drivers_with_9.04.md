---
title: "catalyst 9.3 and 9.4 drivers with 9.04"
date: 2009-04-28
forum: Multimedia Software
---

### Post by kness on 2009-04-28
Hi guys,

I have recently taken the plunge and banished windows from my laptop for good and so far i'm loving ubuntu. Its just worked from the start and I didnt need to install whole bunch of drivers and apps like i would have done for windows.

I have come up agaisnt one problem though. I want to get propriety drivers for my radeon x300 but as i understand it catalyst 9.3 and earlier drivers dont support x 1.6 and catalyst 9.4 doesnt support my card. Is this correct ? And if it is what alternative avenues are there for acheiving reasonable 3D performace and activating compatiz(sp?).

I thing i am using the xserver-xorg-video-ati driver at the moment.

Any help on this would be really usefull.

Thanks,

K

---

### Post by elevashun on 2009-06-11
I'm wondering the same exact thing. I have the same exact setup, but I'm scratching my head because performance with Compiz and Flash Videos are subpar on my system. 

Anyone have any ideas?

---

### Post by Beinrich on 2009-06-11
If you want to use the propriety driver you have to use Ubuntu 8.10.

If you want to use Ubuntu 9.04 you have to use the opensource driver (or one of them, Im not familiar with them).

---

### Post by krozzie on 2009-06-20
I too am having troubles with support for the integrated X1200 ATI. 
Catalyst 9.3 is supported by AMD, the xorg-server 1.6 on ubuntu 9.04 is not.

["Which cards does ATI no longer support? The ATI Radeon 9500-9800, X300-X2100, Xpress. See the complete list here. If your card is on that list, you are restricted to the 9.3 driver - however since 9.3 driver doesn't support xorg-xserver 1.6, it will not work with Jaunty! This guide currently is for installing 9.6. !!!SO BE CAREFUL!!! "]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installation")

Time for a new motherboard? or a recent video card? Downgrade to Ubuntu 8.10?

Hope this info helps out someone.

---

### Post by doublemike on 2009-06-23
For what it's worth, I'm in the same boat. I was running well on 8.10 and foolishly upgraded to 9.04. I probably should have checked the issues first. grrr

Mine card is on a laptop, so I'm sure I probably have fewer options. I'm operational but I get this very annoying flicker. I booted with older distros from CD and they were all solid. I'm just pissed at the time it is costing me to deal with this mess. I've been happy with Ubuntu up until this point.

---

### Post by segalerez on 2009-11-24
I've complained to AMD:

[http://emailcustomercare.amd.com/](http://emailcustomercare.amd.com/)

(I'm not sure they're responsible for this lack of support though).

---

