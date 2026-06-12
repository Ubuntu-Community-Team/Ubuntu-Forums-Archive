---
title: "Horizontal Screen Flicker on External Monitor"
date: 2008-06-20
forum: Multimedia Software
---

### Post by activefx on 2008-06-20
Whenever something is loading or there is motion on the screen (so pretty much all the time), there is a horizontal flicker on the external monitor (Westinghouse LCM-22w3) connected to my laptop (HP dv1040us). I think the problem stems from the Intel 855GM chipset. I've tried a couple of fixes I found online such as 915 resolution and fooling with xorg.conf and the screens & graphics settings. Could it be because the refresh rate is stuck on 60hz? It was running at 75hz when I had windows on the laptop and it worked perfectly, but now 60hz is the only available option. I'm using ubuntu 8.04. 

Anyone have any ideas how to fix this?

---

### Post by Pjotr123 on 2008-06-20
1. disable visual effects (too heavy for your card):
[http://ubuntutip.googlepages.com/tipsandtweaks](http://ubuntutip.googlepages.com/tipsandtweaks)
(number 5 )

2. Applications - Accessories - Terminal
type:
```
gksudo displayconfig-gtk
```

---

### Post by activefx on 2008-06-20
There is no difference with visual effects disabled. 

I also tried several different setting combinations with displayconfig-gtk and couldn't find any that helped. 

Thank you for the suggestions though.

---

### Post by T.J. Crowder on 2010-11-18
Did you ever find any resolution (no pun) to this? If so, if you could point me to where you found the answer, I'd appreciate it. I'm getting much the same thing, with a desktop based around the Intel DH57JG board (which uses the Intel H57 Express chipset). I managed to work around it (purely by accident) with xorg.conf with my previous monitor, but not having any luck at all with my new BenQ G2222HDL...

Thanks,
--
T.J. Crowder

---

