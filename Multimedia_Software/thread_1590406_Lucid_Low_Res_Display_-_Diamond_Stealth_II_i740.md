---
title: "Lucid Low Res Display - Diamond Stealth II i740"
date: 2010-10-07
forum: Multimedia Software
---

### Post by pgmer6809 on 2010-10-07
I have just installed Lucid on a P4 machine.
THe machine came with a Diamond Stealth II AGP 8M graphics card.
Under XP I have no problem getting 1280 x 1024 resolution from it.
I want to convert it to Ubuntu for my son.
I installed Lucid, but I can only get 800x600 resolution on the display.

1. The Admin=>Drivers menu shows no proprietary drivers installed.
2. There is no /etc/X11/xorg.conf file.
3. dmesg | grep drm returns nothing interesting.
4. dmesg | grep modesetting does not return anything.
5. lspci -nn | grep VGA returns: intel i740 AGP accelerator
6. glxinfo was not installed. I installed mesa-utils, then ran it.
   glxinfo | grep vendor returns Brian Paul
7. there is no /usr/share/ati directory
8. Catalyst package description says it is for Radeon cards. Could I use it with a Diamond Stealth card?

Any other suggestions?

Thanks,
pgmer6809

---

