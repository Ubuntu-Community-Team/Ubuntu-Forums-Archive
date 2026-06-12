---
title: "[SOLVED] can't move main window of audacious"
date: 2008-12-19
forum: Multimedia Software
---

### Post by ameno on 2008-12-19
hoi
im on ubuntu 8.10 without compiz. just plain metacity.
i normally use it with main window + playlist window shown.
after i installed it, i could normally move it around like winamp under windows. now i cant.
when i try to move it (i.e. grabbing the top of the main window and moving the mouse) the main window remains where it was, only the playlist window moves around (i looks like the pl window is moved as it would be attached to a moving ghost main window == works just like normal).
if i use alt+mouse i can move the main window (alone). if i enable window decorations i can move it too (alone).

any hints? google showed nothing except a gentoo bug report and this thread without a solution or cause:
[http://ubuntuforums.org/showpost.php?p=5189821&postcount=3](http://ubuntuforums.org/showpost.php?p=5189821&postcount=3)

---

### Post by ameno on 2008-12-23
*bump*

ANY hint how to debug this appreciated!

---

### Post by ameno on 2008-12-25
wtf... it works again

no idea why. :(

---

### Post by ameno on 2008-12-27
and gone again.

even without reboot or logout (although it happens with reboots/relogins too).


and i noticed that the windows get places at coordinates 0,0 at startup and after restoring them from the tray icon.
but i think thats not related and a metacity "thing" (im not sure its not intended)

---

### Post by ameno on 2009-01-01
seems that i have messed aroung too much in gconf...
/apps/metacity/general/disable_workarounds=true == bad bad idea.

broke xchat, audacious, pidgin and probably more.

---

### Post by ChEeZeBaLL on 2009-03-18
I am having the same problem; I cannot move the main Audacious window. I am using KDE 4.1

---

### Post by jordicm on 2009-03-25
Same problem here.

I reported the problem a weeks ago. Here is my full description:
[http://ubuntuforums.org/showpost.php?p=6893388&postcount=1]("http://ubuntuforums.org/showpost.php?p=6893388&postcount=1")

Also I found that there is no problem running Audacious as root.

I've tried reinstaling the aplication with no luck. Up to date this is only application I have with this problem.

---

### Post by jordicm on 2009-03-25
Ok, problem solved. I deleted ~/.config/audacious/

---

