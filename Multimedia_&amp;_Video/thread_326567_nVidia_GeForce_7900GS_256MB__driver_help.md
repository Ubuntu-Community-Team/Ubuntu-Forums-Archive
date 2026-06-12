---
title: "nVidia GeForce 7900GS 256MB  driver help"
date: 2006-12-27
forum: Multimedia &amp; Video
---

### Post by tonythetiger on 2006-12-27
ok i am new to linux  and  am haveing a heck of a time geting my nVidia GeForce 7900GS 256MB PCI-E x16 Video Card the same one that this guy here has [http://ubuntuforums.org/showthread.php?t=252557&highlight=0292%29](http://ubuntuforums.org/showthread.php?t=252557&highlight=0292%29)  it has an id of 0292  
i have Ubuntu Edgy 6.10 i got to this guide here  [http://ubuntuforums.org/showthread.php?t=281823](http://ubuntuforums.org/showthread.php?t=281823) while looking at it and doing a bit of reading  i found the person that pointed to the guide tseliot's  webpage and found a script  called envy  so i tryed it and it told me that my card was not supported so i went back to nvidias page and looked up the new driver Version: 1.0-9746 and looked up suported cards here [http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html) and my card is there "GeForce 7900 GS 0x0292"
so i looked up that ver in synaptic package manger and found it i think it was from tseliot's  repository   here [http://www.albertomilone.com/drivers/edgy/latest/32bit](http://www.albertomilone.com/drivers/edgy/latest/32bit) on  so i installed it  and re booted but my card is still listed as unknown  0x0292  by the way i am useing my my onbord right now  so what am i missing? i also have HIS Hightech Radeon X850XT HX85XTQ256-3TOEN IceQ II Video Card if my 7900gs wont work if both cards are sol and i have to buy a new gfx card so be it i am done upgradeing windows,  xp pissed me off and vista looks even worse so here i am  this is my first time ever useing nix so go easy on me.

---

### Post by tonythetiger on 2006-12-28
oh one more thing i forgot wen i boot ubuntu  it says 

[numbers] pci cannot allocate resources  to region 0 [ numbers]

five times  the numbers are different  and the regions are 0,0,52,0 in that order i would write the numbers down but it goes away fast if it matters there has to be some sort of boot log i just dont know how to get to it  also i guess i could take a pic with my digtal cam  any other info you need to help me let me know

---

### Post by tseliot on 2006-12-28
> **tonythetiger said:**
>  i found the person that pointed to the guide tseliot's  webpage and found a script  called envy  so i tryed it and it told me that my card was not supported
Try envy again and continue the installation of the driver even if envy thinks that your card is not supported.

---

### Post by tonythetiger on 2006-12-28
i went back to the guide and tryed method one and it worked.  so thanks for the help. it still listed as unknow in device manager ( i am guessing that is normal) but it is listed in the nvidia settings and it works so i am happy. it is much smoother now again thanks for the help not near as hard as i thought this was going to be :-D

---

### Post by tseliot on 2006-12-28
> **tonythetiger said:**
> i went back to the guide and tryed method one and it worked.  so thanks for the help. it still listed as unknow in device manager ( i am guessing that is normal)
Yes, it's normal

---

### Post by bccpdx on 2007-09-27
As an FYI (note the gap in post dates), I *just* got the SLI-enabled "BFG" edition of the Geforce 7900GS-OC, 256MB GDDR3, PCI-E.  (Only bought one, though.)  It's installed on an AMD 64 X2 running with 4GB of 800MHz RAM, under Dapper Server LTS + Kubuntu desktop (added to the default LAMP install with a single apt-get).

The unaccelerated driver came up fine, but of course that's not why one buys a card like this one.  :D  Tore my hair out for a while, even broke the system temporarily (it lost the abilty to run modprobe; weird!) and recovered it... then discovered this thread, and **envy** got it running accelerated in almost no time.

I used envy's text mode under the unaccelerated X GUI; the GTK version died -- but the text mode worked fine once I got past the python dependencies.  (Hey, I only finshed putting the box together this afternoon, and it's still a very minimal install.)

The mention of "apt-get install -f" in the envy FAQ helped immensely with that, by the way. Moral for lurkers -- FOLLOW THE LINKS in TSEliot's sig!!!

**Molto bene, Alberto! Mille grazie!**

---

