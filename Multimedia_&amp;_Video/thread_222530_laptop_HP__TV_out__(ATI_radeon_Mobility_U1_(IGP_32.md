---
title: "laptop HP  TV out  (ATI radeon Mobility U1 (IGP 320m))"
date: 2006-07-25
forum: Multimedia &amp; Video
---

### Post by stuelestue on 2006-07-25
Hello,  this kind of message seems to be posted many times but i truly did not find any help for me.
I have a true problem with my ATI card. I tested at least four different methods in vain. I am thus intereted in any advice. 

Portable HP Compaq nx 9005, video card ATI radeon Mobility U1 [IGP 320m], processor AMD athlon XP
Dapper just installed 

Objective: to be able to play my divX on my TV most simply possible (I do not care of the 3D)  

Questions to take in the order: 
- Stage 1: Dapper proposes updates. Should they be done before anything else?
- Stage 2: should tv out work with booting with tv on ? Is there any file to configure. Out of the box direct rendering is on with mesa 3D.
- Stage 3 :should the kernel absolutely be updated to k7? By the terminal or synaptic? Which order or which packages to install?  - Stage 4: which drivers to choose: ATI, radeon or fglrx? How to install them? Did somebody succeed in installing the ATI driver (fglrx) without problem? 
- Stage 5: according to is stage 4, necessary to launch dpkg-reconfigures xserver-xorg? 

Finally 2 complementary questions:  
- is there simpler to activate the exit TV?  
- am I it only guy in France and in the world to try to install ubuntu under this portable? 

Thanks you all for help

---

### Post by stuelestue on 2006-07-26
more :

fglrx driver does not work
radeon and ati both works with 250 fps on glxgears.

atitvout and gatos do not work.

Nobody using a card that do not work with fglrx driver but able to play on tv ?

Thanks

---

### Post by Okami on 2006-07-28
First, sorry for my english, its terrible but I hope you understand.

Found the link to your topic from amilos yahoo group.

I was going to test tv out with this card tomorrow so I really want to know about tv out too.

Before I was sing the k7 kernel but someone told me that the 686 have more support, but either should be fine. 
From terminal or synaptic? Either should be fine from what I understand (still beginner :p ) Choose linux-k7 from synaptic and it will install everything.

About the drivers, I think there is no drivers for this card. The ati drivers is for newer card. But I may be wrong.
You can get better fps on glxgears if you install the latest from here [http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/) For this you also need linux-headers-k7 from synaptic.

---

### Post by stuelestue on 2006-07-31
Here is the solution, IN FRENCH.
[http://forum.ubuntu-fr.org/viewtopic.php?id=51647]("http://forum.ubuntu-fr.org/viewtopic.php?id=51647")
Just ask if you want me to translate it in english.

I will appreciate have your options for the radeon driver with that card. I have 250 fps with glxgears -printfps.

Thanks
Stue

---

### Post by Okami on 2006-07-31
Thanks, it was not so hard to get it work actually (tv out with atitvout), but I did something wrong on the TV so I had no sound at first, but I got help =)

I have 2244 frames in 5.0 seconds = 448.703 FPS.

---

