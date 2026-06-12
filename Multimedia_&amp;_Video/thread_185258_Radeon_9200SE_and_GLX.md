---
title: "Radeon 9200SE and GLX"
date: 2006-05-31
forum: Multimedia &amp; Video
---

### Post by gumbald on 2006-05-31
I have just upgraded to Dapper, however I have one main question... Is GLX going to work on my Radeon 9200SE (RV280)?

I have tried the Kororaa live CD, and it didn't, as reported on their website. However, on [http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL](http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL) there are contradicting statements...

>     *  Radeon 9200SE
          o Chipset: RV280 (5964)
          o Driver: ati-drivers-8.24.8
          o Notes: tested on FC5, using this repo [http://users.telenet.be/quenta/repo/](http://users.telenet.be/quenta/repo/) and fglrx drivers came from Livna repo 


and further down (under "seemingly unsupported"):

>     ATI Technologies Inc RV280 (5964) [Radeon 9200SE] (with ati-drivers-8.22.5, Distorted screen)

    * Works for me. Got a distorted screen in rootless mode, but standalone server (using startxgl script) works perfectly on xorg drivers (modular xorg-x11 7.0-r1) 


Can anyone give me a definite answer as to whether it's going to work before I potentially mess up my system...? And explain the method of the above claims that it does work if so :)

TIA

---

### Post by simplyw00x on 2006-06-01
I assume you're talking about **XGL** not **GLX**. Based on such a foolish assumption, let me continue! (I have a 9200SE)

I never managed to get XGL working with the fglrx drivers. Maybe this has changed recently, but XGL on fglrx results in the known (but mysterious) "whole-screen distortion bug". What _did_ work, however, was running XGL using the radeon drivers. Use 'radeon' instead of 'fglrx' in xorg.conf, make sure you're loading the right kernel modules and that's basically it viz. chages. XGL and compiz should then work.

Unfortunately, then there's no 3D acceleration for games, Frostwire and some other Java apps are unusable and it's a bit of a CPU hog. I therefore tried AIGLX. It worked well with the radeon drivers (until the upgrade where they made you start recompiling DRI modules). I've done a fresh install since and this info may be out of date by now, but good luck to you.

---

### Post by samoht on 2006-06-01
Hi,

I installed XGL on dapper with Radeon 9200SE and "radeon" opensource DRI drivers. The card is supported, but it's to slow. Switching workspaces takes several seconds, black artifacts all over the screen, etc...

I can't tell about the proprietary drivers though...

---

### Post by gumbald on 2006-06-01
I have no idea how I managed to call it GLX twice!

Can you point me to the best tutorial for all this (I've found lots of part tutorials and ones that just don't make sense!)? Would like to try it, can go back if I don't like it... If not, got my eyes on a nvidia 6200 or such :)

---

### Post by gumbald on 2006-06-01
Changing "fglrx" to "radeon" seemed to work as it allowed me to login to the XGL session I'd created in a tutorial. However, once in graphics were terrible, taking ages to refresh everything and not at all bearable.

I'll get a new graphics card (I inherited this one anyway) but for now can anyone tell me the setup that will get the most out of my 9200SE?

---

