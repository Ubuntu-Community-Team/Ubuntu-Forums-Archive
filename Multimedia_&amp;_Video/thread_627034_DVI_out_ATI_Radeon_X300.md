---
title: "DVI out ATI Radeon X300"
date: 2007-11-29
forum: Multimedia &amp; Video
---

### Post by aerorahul on 2007-11-29
Hi,
I run 7.10 with the Display Card: ATI Radeon X300 
It has both VGA and DVI out.
Till yesterday I was using the VGA out for my 17" CRT. It had configured automatically everything using xserver-xorg.
I switched to a 22" widescreen LCD monitor (still on VGA) and configured using xserver-xgl using the command sudo dpkg-reconfigure xserver-xgl
Everything worked, including compiz and the cube rotation, etc.
Today I bought a DVI cable and connected using it and that is when everything broke.
Again, I tried the xgl reconfiguration, but the log-in screen breaks immediately each time it boots and then the only way to access a terminal is Ctrl+Alt+F1. 

lspci |grep -i 'ati'
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc [Radeon X300SE]

Any thoughts on how to configure a ATI Radeon X300 Card with DVI out to use with a 22" 1680x1050 LCD display will be apprecited. 

Also, the only way I can get to a desktop without breaking is if I use the Failsafe Gnome session after I have configured xserver-xorg. Here the restricted drivers for ATI are disabled and enabling them simply breaks it again.

Thanks for reading.
Cheers.

---

### Post by aerorahul on 2007-12-02
bummmp !! help?? someone, anyone :(

---

### Post by aerorahul on 2007-12-02
bummmp !! help?? someone, anyone :( Moderator?? Support?? User ?? Beginner??

---

