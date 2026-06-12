---
title: "unable to switch back to gnome?"
date: 2011-04-01
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by TDK800 on 2011-04-01
upgraded 10.10 to 11.04
logged out, no option to choose different desktop
installed gnome, still no option

---

### Post by dino99 on 2011-04-01
when you get gdm, choose ubuntu classic on bottom screen before logging

---

### Post by TDK800 on 2011-04-01
gdm is installed. The problem is there's no selection menu on the bottom panel like there should be.

---

### Post by LKjell on 2011-04-01
You can hack your way through. Log into the console.
In /usr/share/gnome-session there should be a file named ubuntu2d.session and one with ubuntu-gnome.session can't remember the name.
Back up ubuntu-gnome.session and replace the content of ubuntu2d.session
to ubuntu-gnome.session

Otherwise you could just edit your ~/.dmrc file to reflect that you use ubuntu-classic.


BTW if you select your username then you get a chance to select which session you want to log into

---

### Post by TDK800 on 2011-04-01
Thanks. The problem was that the desktop selection menu appeared on the bottom panel for only part of a second once I clicked the username and then it immediately logged in. I changed it to ask for password before logging in, this way I was able to change the desktop too.

---

