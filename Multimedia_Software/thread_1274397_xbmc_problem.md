---
title: "xbmc problem"
date: 2009-09-24
forum: Multimedia Software
---

### Post by nush on 2009-09-24
hi all
i've been trying to install xbmc today and all i get is the following message
 sudo apt-get install xbmc
[sudo] password for xxx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  xbmc: Depends: xbmc-common (= 9.04.1-jaunty1) but it is not going to be installed
        Depends: xbmc-skin-pm3-hd (= 9.04.1-jaunty1) but it is not going to be installed
        Depends: xbmc-web-pm3 (= 9.04.1-jaunty1) but it is not going to be installed
E: Broken packages

ive checked the multiverse and universe option are ticked.

thanks

---

### Post by bgiannes on 2009-10-12
[http://www.xbmc.org/forum/showthread.php?p=185738](http://www.xbmc.org/forum/showthread.php?p=185738)


or


[http://xbmc.org/wiki/?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu%2C_a_Step-by-Step_Guide](http://xbmc.org/wiki/?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu%2C_a_Step-by-Step_Guide)

---

### Post by jerrodbug on 2009-11-08
yeah--i've read both of those, and still cannot get it to work.  any other ideas?  im pretty new to ubuntu.

---

### Post by punia1979 on 2009-11-09
ye I have the same problem... I was installing ubuntu 9.04 on one of my friends laptop (it is at least 10 times as I am doing it) standard procedure I customize software as allways... gnome commander, k3b, skype etc... but when I am trying to install xbmc I get the same errors? is the xbmc SVN damaged or something?

---

### Post by punia1979 on 2009-11-09
think problem might be related to libssl....

---

### Post by pinenut on 2009-11-10
I've just installed ubuntu 9.10 (karmic) and then xbmc following the direction given in the wiki ( **[http://tinyurl.com/y99khtv](http://tinyurl.com/y99khtv) ). **I did not have any problem whatsoever while installing xbmc. 

The only problem I have with xbmc is that my USB wireless mouse is working so poorly that I had to quit. Unless I solve this problem, I may not be able to use it at all.

Mouse: part of Microsoft Wireless Optical Desktop 700
Motherboard: Asus M2NPV-VM

Can something be done withourt changing the mouse?

[Solved]
I've solved my mouse problem by installing the proprietary driver for nVidia  Geforce 6150 graphic card.
It was quite simple to do it from System> Hardware Drivers> Proprietary driverXXX(recommended)

---

### Post by punia1979 on 2009-11-11
the problem is not with the new release but with older releases...

---

### Post by sdowney717 on 2009-11-18
if you run karmic then you have to use xbmc 'camelot' right now in alpha 2
their is info on their site as to enabling the repository

---

