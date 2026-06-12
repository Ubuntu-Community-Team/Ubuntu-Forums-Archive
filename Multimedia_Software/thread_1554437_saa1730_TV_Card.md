---
title: "saa1730 TV Card"
date: 2010-08-16
forum: Multimedia Software
---

### Post by Narsill691 on 2010-08-16
[B]My original post was for help with the Phillips saa7130 tv card, sorry for the typo.....

I installed Ubuntu 9.10 Karmic Koala and installed TVtime then entered the following commands and my Capture card works great.

$ sudo rmmod saa7134_alsa
$ sudo rmmod saa7134
$ sudo modprobe saa7134 card=42
$ gksu gedit /etc/modprobe.d/alsa-base.conf
  [/B]*_When alsa_b__ase.conf is opened find the following line_*[B]*....*
# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
  [/B]_*then add this right after*_[I]....
[/I][B]options saa7134 card=42
Now you should be good to go, or if you need to change the card # check here ---> [/B][http://ubuntuforums.org/showthread.php?t=1242015&highlight=saa7130](http://ubuntuforums.org/showthread.php?t=1242015&highlight=saa7130)
**That thread also lists tuner #'s, these can be used on modprobe but they will cause an error if you add the tuner to alsa_base.conf.  That thread also has detailed instructions if mine don't work for you.**
** My issue is now with my ATI Radeon x1650gt 512 AGP card.  I installed drivers through Envyng and it made things worse, I can't change my 22" widescreen the more than 1024x768 and I can't use it as my primary monitor.**

I have tried installing the driver using sh but it won't install the packages b/c they aren't in debian format.  I have already downloaded the most recent ATI drivers from the mfg site, I just need suggestions on how to install them.  Any suggestions are greatly appreciated!!

---

### Post by Narsill691 on 2010-08-17
sh --listpkg gives me:
    Ubuntu Packages:
        Ubuntu/7.10
        Ubuntu/8.04
        Ubuntu/8.10
        Ubuntu/9.04
        Ubuntu/gutsy
        Ubuntu/hardy
        Ubuntu/intrepid
        Ubuntu/jaunty
        Ubuntu/source
....I have tried Ubuntu/source and then it can't find the ".changes" file and wants me to manually install the packages it created.  I don't know how to install .tar.gz packages manually, and sh won't install them b/c they aren't in debian format.  Please help?!?!? I am lost!!

---

