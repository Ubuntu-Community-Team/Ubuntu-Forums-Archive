---
title: "Problem - &quot;Losing&quot; video driver nvidia and reverting to VESA"
date: 2008-04-05
forum: Mythbuntu
---

### Post by phuturism on 2008-04-05
Running mythbuntu 7.10 on a P4 dual with an nVidia GeForce FX 5200

Installs and works great with the install cd recognising the video card and prompting to install with proprietary driver.

I'm running it through a TV with svideo out and the standard resolution is hard to read (for menus and so on) - if I change the screen resolution this helps.  This seems to however screw up the driver so on reboot I get an "LIRC not configured" message  - is this related?  - and also have to start in "low graphics mode" - looking at the video card settings the system has reverted to the Vesa generic driver.

I can't find the exact nvidia driver using the video card driver interface and any nvidia choices seem to fail and it reverts back to the vesa generic driver.  As I have done a lot of tweaking including an Australian XML tv grabber configuration I really don't want to reinstall again!!!  This would be about my 4th reinstallation as I am a slow learner :(

Can I edit the xorg.conf manually file to use the nvidia driver ?  If so, what settings should I use?  Or any other suggestion to fix the problem gratefully accepted.

I should also say that once up and running I generally have done a software update so this also could be a potential source of problems with the driver.

Help!!!  thanks

---

### Post by phuturism on 2008-04-05
Belay that last request!!!!   I managed to fix the problem by doing

> sudo nvidia-settings

and then > sudo nvidia-xconfig

I had tried this before but got stymied when pkg-config was not installed.  All seems to be good now.

---

