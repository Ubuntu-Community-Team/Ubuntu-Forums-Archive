---
title: "Soud Blaster: Sound goes in bursts"
date: 2011-11-13
forum: Multimedia Software
---

### Post by oryctes on 2011-11-13
I just installed ubuntu 11.10 in a new computer with a SoundBlaster X-Fi Xtreme, which the system identifies (along with a NVidia sound card) correctly.

 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfa080000 irq 17
 1 [Creative       ]: HDA-Intel - HDA Creative
                      HDA Creative at 0xfa100000 irq 16

The sound works, but at burts. It constantly goes on and off.
I tried disabling the first card as I don't use it, but the situation didn't change.

Any ideas?

---

### Post by Rodney9 on 2011-11-13
Sound troubleshooting
Have a look at this site - 

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

and this one, more up todate, but still a work in progress, however very good - 


[https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit](https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit)

Rodney

---

### Post by larrypg on 2011-11-14
Hello,

You are not alone with getting an X-fi Xtreme to work with 11.10. I have not got it working yet.  I am curious what that second link to google docs is because it is saying not found.  Hopefully someone will come up with an answer to this problem.

---

### Post by Rodney9 on 2011-11-14
Sorry , wrong address, here is the correct one to  [Sound Troubleshooting Guide for Ubuntu 10.04, 10.10, 11.04 and 11.10]("https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit")

Rodney

---

### Post by oryctes on 2011-11-19
Thank you Rodney,

But bad news for me. According to the [[COLOR="Blue"]ALSA Vendor Matrix[/COLOR]]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs"), my card (X-Fi Xtreme Audio [PCIe] CA0110) is listed in plain words as *'does not work'*, without any more details :-(

I found the following bug that confirms it:

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/889698](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/889698)

I also filed a bug in the ALSA bug tracking system. I presume that for the moment there's little I can do but wait.

---

### Post by larrypg on 2011-11-19
Hello,

At least for me the card works fine in 11.04 but does not in 11.10.  I just went back to 11.04 until it gets fixed.

---

