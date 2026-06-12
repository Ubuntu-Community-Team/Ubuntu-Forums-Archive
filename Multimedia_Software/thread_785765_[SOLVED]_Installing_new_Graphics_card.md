---
title: "[SOLVED] Installing new Graphics card"
date: 2008-05-07
forum: Multimedia Software
---

### Post by indiana_crook on 2008-05-07
I have decided to purchase a new graphics card to replace this ATI Radeon.  My question is this... I'm not a computer gooroo, so bare with me here.  What all do I need to do in order to ensure that the new one is going to work with ubuntu.  It's being replaced with an Nvidia GEFORCE 7600.  Am I gonna have problems when I take out the ATI and replace it with the Nvidia, or is it all plug and play?

---

### Post by overdrank on 2008-05-07
> **indiana_crook said:**
> I have decided to purchase a new graphics card to replace this ATI Radeon.  My question is this... I'm not a computer gooroo, so bare with me here.  What all do I need to do in order to ensure that the new one is going to work with ubuntu.  It's being replaced with an Nvidia GEFORCE 7600.  Am I gonna have problems when I take out the ATI and replace it with the Nvidia, or is it all plug and play?

Hi and when you are ready to install the graphics card you will need to uninstall the ati drivers. Then I would suggest you look at Envy for the installation of the new card.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
When you boot the system with the new card you will likely see the blue screen xorg failure. Then you can reconfigure your xorg and reboot then use Envy to help with the drivers. What version of Ubuntu are you using?

---

### Post by indiana_crook on 2008-05-07
I'm using Hardy

---

### Post by ibr3ak on 2008-05-08
Yep try what overdrank suggested, I've recently had to replace a number of vid cards on my machines, when you install a new card it will most likely fail and go to blue screen, if it does, reboot your system and when at grub choose the recovery mode which will boot you into root, then just do:

```
 dpkg-reconfigure xserver-xorg
```

what I usually do is change the name of the vid card and leave the rest of the options on default, and only worry about everything else once I know the xorg is fine and I can boot into x.

---

### Post by indiana_crook on 2008-05-11
I just put the new card in the computer, and ubuntu did the rest for the most part.  I had to reconfigure xorg, and after that I got the dreaded white screen after log in, but after I fixed all that, The drivers installed themselves.  Good job Ubuntu!!!

---

