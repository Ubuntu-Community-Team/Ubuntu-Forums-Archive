---
title: "[SOLVED] nvidia 8800 GS driver trouble"
date: 2008-08-14
forum: Multimedia Software
---

### Post by stoneage on 2008-08-14
Just tried to install a Gainward 8800GS graphics card and it went badly.
I used Envy to install drivers and the resolution is now stuck on 800 x 600.
Also the keyboard is affected, keys don't respond to what they should be £
is now # etc. Couldn't log in because I was typing the wrong(apparent) password.

I keep getting this under nvidia x server settings[ATTACH]81594[/ATTACH]
but when I run it I get this C[ATTACH]81595[/ATTACH] 

organic@organic-desktop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GS (rev a2)
organic@organic-desktop:~$

Lost, need help. Can someone advise what to configure?

Ubuntu 8.04 64 bit

chris.

I'm looking at xorg.conf but I don't know what to alter
Preferred resolution is 1440 x 900
Needless to say the problem persists even with the card removed.

---

### Post by stoneage on 2008-08-14
Removed the envy installed drivers and installed manually then cleaned up the mess made by the envy induced rewrite of xorg.conf.

---

