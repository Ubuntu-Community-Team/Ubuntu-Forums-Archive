---
title: "LiveDVD &amp; problem w. GeForce 6600GT agp"
date: 2006-03-05
forum: Multimedia &amp; Video
---

### Post by foxmulder on 2006-03-05
Hi,

I want to run Ubuntu on my PC but to test it out I figured I download the LiveDVD which holds both the live version and the install.

Everthing goes well, up untill the point where the xserver starts up (Gnome), then the display goes all garbled and all I can do is switch to a console and reboot.

Off course I'm afraid it will do the same when I install the whole deal.

What is a bit disapointing is the fact that all other live CD's I tried (Kanotix, Knoppix, SUSE Live etc. etc.) all do run without problems

(I think Ubunutu should ask for confirmation about whatever hardware it thinks it detected so you can correct any discrepancies.)

Btw: the video card is a GeForcxe 6600 GT AGP (not Pcie) from Leadtek.

Anyone have any idea if/how I can fix this for BOTH the Live environment and when I want to install it for real?

Thanks in advance!

---

### Post by TheDarkPT on 2006-03-05
Hi, I have the exact same problem, the only difference is that I have a GeForce 6600 non-GT, and it also happens on Fedora Core 4.

Any help would be greatly appreciated

---

### Post by Jason_25 on 2006-03-05
The old version of the open-source nv driver does not support the 6600.  You need to use the vesa driver or the closed-source nvidia driver.  Obviously, this would be hard to do with the live disc, but after an install you can change it.

---

### Post by knalle on 2006-03-05
i got a geforce 6800 GT AGP and have no problem with the live cd or the install, when you come to the xconfig, select **vesa** as driver and finish up the install, **then** install the **nvidia** drivers, that works for me

---

### Post by TheDarkPT on 2006-03-05
thanks for the reply, just found out this topic:

[http://www.ubuntuforums.org/showthread.php?t=136971](http://www.ubuntuforums.org/showthread.php?t=136971)

that says exactly that!

thanks again!

---

