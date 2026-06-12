---
title: "Disappearing support for ATI rage 128 video"
date: 2008-05-07
forum: Multimedia Software
---

### Post by jeffs0413 on 2008-05-07
I am composing this message using a old dell desktop (gx240)with a p4 chip and ati 128 rage pro for video support.  I am happily running ubuntu 7.10 (gutsy gibbon).

7.10 autodetected the graphics card and configured xserver for maximum resolution.  It allowed me to select 1280x768 resolution.  Everything was good.

I installed 8.04 on a exact duplicate machine.  Autodetect for the ati card did not work.  I could not select display resolution above  800x600.  I tried dpkg-reconfigure xserver-xorg to manually detect the card. It modified xorg.conf to a maximum resolution of 640x400.

What is happening?  Graphics support for this ati card was great on 7.10 but is awful on 8.04. I have read the sticky entry about support for ati cards(300+ entries)but have no answer.

I had hoped to replace windows based desktop with 8.04 lts but this situation is not very encouraging.  Any answers to this situation will be appreciated.

jeff

---

### Post by avtolle on 2008-05-07
Jeff, I've the same ati card on two Mac G4 Cubes. The simple(?) answer is to grab a copy of your working 7.10 /etc/X11/xorg.conf file and manually edit the one in 8.04. Pay attention to the lines in the 7.10 file about Device, Monitor and Screen (esp. the modes lines), and the possible extra Section "DRI" at the end of the 7.10 file (assuming yours is as is mine, perhaps not safe). Be careful.

---

### Post by avtolle on 2008-05-07
The above is based upon my presumption that System-->Preferences-->Screen Resolution was not useful to you.

---

### Post by jeffs0413 on 2008-05-07
I tried both of the recommendations above.  Neither solved the problem.  
What troubles me the most is that the support was present in a previous version(7.10). Does the development process break important functions as the kernel versions change?

I use linux running Asterisk and IPcop.  This is my first attempted to place linux desktop in a production situation. Help.
jeff

---

### Post by jeffs0413 on 2008-05-08
For all who stumble on this thread here is the answer to allowing ati displays to work with HH
[http://ubuntuforums.org/showthread.php?t=766826&highlight=ati+rage](http://ubuntuforums.org/showthread.php?t=766826&highlight=ati+rage)
jeff

---

