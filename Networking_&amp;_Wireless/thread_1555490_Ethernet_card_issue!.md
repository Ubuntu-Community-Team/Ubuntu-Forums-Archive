---
title: "Ethernet card issue!"
date: 2010-08-18
forum: Networking &amp; Wireless
---

### Post by s0rc3r3r on 2010-08-18
Hello There
I am new to Ubuntu.Installed it only a week back and I am loving it.

 I am using **Ubunto 9.10Karmic** version.When I installed Ubuntu, my Ethernet Interface card (eth0) was not detected. After going through the Ubuntu Forum, I managed to find the correct driver for my Ethernet card (Aetheros).Compiled it and Installed it on my machine. Things worked fine.I got my 'Wired' network on the Panel.

Yesterday, I updated my Ubuntu for the first time.I installed all the 'Updates' the update manager asked me to install.
After the update and the install. my 'Wired' network disappeared again from the Panel.
I checked the Administration->'NETWORK TOOLS' my Ethernet card was shown not shown in the list.It was listed as undetected.[It was just as before, I compiled and installed the Etherner Driver]

My question is 
1)Why is this happening?
2)Will it happen every-time I update my machine?
3)Is there any way to prevent auto delete of these third party drivers[Which we compiled and installed]
4)Is there anything more we should do when we install third party drivers?Meaning..did I miss any step during the install of the driver?

Thanks in advance!

---

### Post by tarps87 on 2010-08-19
It is possible contained in the update was a new kernel, if this was the case it is highly likely this is why the driver was lost.  This should not happen every time you update. As for auto recompiling and I am unsure of how to do this on Ubuntu but will look into it when I get the chance.
Can I assume that after installing the driver you network card is operational?

---

### Post by s0rc3r3r on 2010-08-19
> **tarps87 said:**
> It is possible contained in the update was a new kernel, if this was the case it is highly likely this is why the driver was lost.  This should not happen every time you update. As for auto recompiling and I am unsure of how to do this on Ubuntu but will look into it when I get the chance.
Can I assume that after installing the driver you network card is operational?

Okay.Thank you for the information. Still learning to understand the new world order of amazing Linux.
wow! is there an auto compiling option or something similar to that! Cool!!
Yeah..Installing the driver again  made my network card operational.
Thank you again for replying

---

### Post by tarps87 on 2010-08-20
This will not work for your driver but it will provide the basis for creating a script to do so.
[http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)
There may be other better methods but I do not know them. Could you post a link to the actual driver you are using and I will have a look at modifying the script when I get chance

---

### Post by s0rc3r3r on 2010-08-20
> **tarps87 said:**
> This will not work for your driver but it will provide the basis for creating a script to do so.
[http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)
There may be other better methods but I do not know them. Could you post a link to the actual driver you are using and I will have a look at modifying the script when I get chance

wow! dude.that script was really cool!


Sure thing buddy!!

Name of the driver file in compressed format is :compat-wireless-2010-08-09.tar.bz2

I downloaded the driver from :[http://wireless.kernel.org/download/compat-wireless-2.6/](http://wireless.kernel.org/download/compat-wireless-2.6/)

Also..one more thing I would like to ask..

Do you have any information whether,the new/upcoming  LTS release of ubuntu will have these drivers bundled with it?

---

