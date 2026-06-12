---
title: "GNOME doesn't work after upgrade"
date: 2010-09-08
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by H0lyGanGs7eR on 2010-09-08
Hello guys, I have just upgraded my Ubuntu to 10.10. I restarted and I got the KDM login screen (my default), but after 3-4 seconds it crashed and i had to login in console, GNOME started only the background and nothing else - no menu, no bar, even no mouse. Help please.

---

### Post by meborc on 2010-09-08
> **H0lyGanGs7eR said:**
> Hello guys, I have just upgraded my Ubuntu to 10.10. I restarted and I got the KDM login screen (my default), but after 3-4 seconds it crashed and i had to login in console, GNOME started only the background and nothing else - no menu, no bar, even no mouse. Help please.

was there any reason why you needed to upgrade to a non-stable ubuntu other than desire to break your system?

:D sorry, no intention to be killing your enthusiasm, but there are warnings up here not to do it on you production (main) machine

now, have you tried booting to the recovery mode... checking the "apt-get update && apt-get dist-upgrade" to see if all updates really did finish updating

in gnome, does alt+F2 open the run window?

do you remember, which packages were removed during the upgrade?

---

### Post by H0lyGanGs7eR on 2010-09-08
Look, I have W7 on my computer too, so it's not a big problem, that i moved on 10.10, problem solved after 2-3 restarts and login in GNOME/Openbox, not Ubuntu Desktop Edition. I'm not enthusiast, I just like to help my favourite distribution so I tested the new version.

---

### Post by meborc on 2010-09-08
> **H0lyGanGs7eR said:**
> Look, I have W7 on my computer too, so it's not a big problem, that i moved on 10.10, problem solved after 2-3 restarts and login in GNOME/Openbox, not Ubuntu Desktop Edition. I'm not enthusiast, I just like to help my favourite distribution so I tested the new version.

ok... good to hear that your system is back up

---

### Post by ranch hand on 2010-09-08
Ah, so you did upgrade to break your system, good for you, welcome to the FUN.

What video card or controller are you using?

This could well be the problem but the cure is pretty specific to the model card you are using.

---

### Post by H0lyGanGs7eR on 2010-09-08
I said GNOME didn't started properly :) , X worked correct, KDE and LXDE worked perfect. My video is GF8500 and works pretty well. I found another problem. I removed my wine1.3.1 and wanted to make a fresh install of Wine 1.3.2 but there is some problem with the dependances. I hope moderators take a look of the forum, it's the easiest way to see where are the bugs in this Beta.

---

### Post by 23dornot23d on 2010-09-08
Cutting and pasting the error - showing what dependancies are missing -  also starting a thread on - Wine Dependancy Problem - may help to resolve the new problem ...... 

But search this section of the Forum for Wine Problems first - to see if any others have posted on WINE not working properly.

---

### Post by ranch hand on 2010-09-08
The devs do not spend time here.  If you have a problem the only way it will get fixed is by filing bug reports or adding to existing ones.

---

