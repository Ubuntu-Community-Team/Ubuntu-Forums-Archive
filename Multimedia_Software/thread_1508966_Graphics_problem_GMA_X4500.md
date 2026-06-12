---
title: "Graphics problem GMA X4500"
date: 2010-06-13
forum: Multimedia Software
---

### Post by halfpint on 2010-06-13
HI,

New to Linux and just dual booted 8.04 Hardy with win xp pro. Need 8.04 so that I can run emc2 on a rtai kernel so upgrading is out at this point. The problem I am having has been discussed but not having any luck with the commands that I see posted in the forums. I don't have a xorg.conf file it does not exist, when I try and create one it does not work. would like to get the onboard graphics working as I don't need alot of power but would be nice to get the native res of my monitor 1366 x 768. Would someone help me with what I need to do first. I know nothing about the commands at this point, just want everything working as it should before I dive in.

halfpint

---

### Post by owain123 on 2010-06-13
Can you upgrade to Ubuntu 10.04?

In terminal type:
sudo apt-get dist-upgrade

This will upgrade your system from Ubuntu 8.04 to Ubuntu 10.04, you should have a better hardware support with 10.04

Hope this helps :)

---

### Post by halfpint on 2010-06-14
Can't upgrade at this point, linuxcnc has not compiled emc2 with 10.04 yet. I am too new at this point to even consider trying to compile a 10.04 RTAI kernel and adding emc2, from what I gather at the Linuxcnc site it is in the works, until then I just wanted to get things working in 8.04.
 
I did alittle more playing around and ran glxgears and was getting 1000fps and better, but still can't get desktop effects to work. I also can't get my xorg.conf file to show when inputting commands as posted on the forums in a terminal, all I get is feed back telling me the file does not exist or if commanded with gedit a blank file.:(
 
What's up? I see onthe forums that some people are having good luck with these intergrated graphics chips and some are not. Does settings in the bios have anything to do with these issues? Different motherboards with same graphics (X4500).:confused:
 
At this point don't see myself giving up winxp.
 
halfpint

---

