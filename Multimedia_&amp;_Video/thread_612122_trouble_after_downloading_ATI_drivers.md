---
title: "trouble after downloading ATI drivers"
date: 2007-11-13
forum: Multimedia &amp; Video
---

### Post by PsyDev on 2007-11-13
Hey I hope someone can fix this problem, I am stuck in low-res and it's painful! I installed ubuntu and it was running fine (7.10).

I was running in 1280x1024 without problem using generic drivers (whatever came with ubuntu). I then got a notification from the OS that ATI drivers were available and so I downloaded them. Unfortunately, when I next rebooted, there was a problem and I was stuck in low-graphics mode. I tried selecting the proper driver when I hit "configure" but it does not save my preference.

After Ubuntu starts, I went to System->Administration->Screens and Graphics. I changed the card driver to VESA (generic) and hit "OK" but I get the same problem on next boot. 
The default that it keeps reverting to is "ATI- ATI Mach 16, Mach 32, Mach64 and RageXL cards"
I am running an ATI Radeon 9600.

Please help!

---

### Post by Mcavity on 2007-11-13
well Im betting the problem is located in your xorg.config file. 
in etc > x11 there are going to be a couple of backup copy's of this file.. try restoring one of those?
I'm not a guru so unfortunately I'm not going to be able to script it for you.

---

