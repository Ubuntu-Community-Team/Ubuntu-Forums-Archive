---
title: "Nvidia drivers broke GUI"
date: 2010-03-04
forum: Multimedia Software
---

### Post by OzzyFreakDude2 on 2010-03-04
Hello
I have a desktop with an integrated Nvidia graphics chip.  I installed the Nvidia drivers through ubuntu's driver manager.  It worked fine, but some games turned off my monitor with an unsupported video mode, so I installed an older version of the drivers through a *.run file.  I had to turn off gdm and install it without graphics, through terminal.  When I tried to reboot, the graphics were all messed up.  The screen was misaligned, and the highest screen resolution I could use was 700 by something.  So I figured that if I could just uninstall the drivers, I could reinstall the correct driver and things be okay.  Then my gui broke.  When I try to run startx, it gives me the "fatal server error: no screens found".  

If I could just purge and remove all traces of the nvidia drivers and/or use Ubuntu's built-in video driver, I should be able to reinstall whichever version of the driver I want and be good.  However, I can't figure out how to.  I've seen where people say to just apt-get-remove --purge nvidia-glx, but it tells me that I don't have nvidia-glx installed to begin with.

I'm using Karmic x64
thanks in advance

---

