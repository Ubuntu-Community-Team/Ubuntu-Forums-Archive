---
title: "Flash videos won't play sound anymore"
date: 2010-02-15
forum: Multimedia Software
---

### Post by Cooter2543 on 2010-02-15
I was having problems with pulseaudio, which I eventually cleared up. Now sound works on everything except flash videos and games. I have tried to reinstall adobe-flashplugin in synaptic, but I get this:

E: adobe-flashplugin: subprocess installed pre-removal script returned error exit status 2

When I try to remove Adobe Flash Plugin 10 in Ubuntu Software Center, I get this:

installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 254674 files and directories currently installed.)
Removing adobe-flashplugin ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing adobe-flashplugin (--remove):
 subprocess installed pre-removal script returned error exit status 2
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 adobe-flashplugin


I primarily use Opera, but flash videos do not work in either Opera or Firefox.

---

### Post by Scotchifer on 2010-02-15
I'm having the same problem. Running 9.10, and flash sound wont work....any suggestions? ](*,)

---

### Post by lovinglinux on 2010-02-16
For 32bit see [this](http://lovinglinux.megabyet.net/?page_id=220#Removing-Conflicting-Plugins-2).

For 64bit see [this](http://ubuntuforums.org/showthread.php?t=1358591).

---

### Post by Cooter2543 on 2010-02-16
I did get mine to work after fighting it for about two hours. I tried many things recommended various places, and none of them worked immediately. Then I rebooted and the sound was working again, so I can't pin-point what actually worked for me. I thought we were passed the days of rebooting every 5 minutes after something gets changed?!?

Anyways, thanks to lovinglinux for the link, and good luck to Scotchifer.

---

