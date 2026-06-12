---
title: "Gnome3/gnome-shell occurrences"
date: 2011-04-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Quackers on 2011-04-12
I have noticed something today, when booting using gnome-shell.
I have a laptop and when I boot when it's plugged in to AC power I am getting a pop-up stating that "a system problem occurred" and it asks if I want to report it or cancel.
However, if I boot when the power lead is detached I get several pop-ups.
I get 3 "system problem occurred" pop-ups, one after the other. I then get a pop-up saying that the gnome shell needed to restart (report or cancel). I get one saying that the gnome settings daemon has crashed and another saying the gnome-power-manager failed to start.
The battery icon does not then appear in the top panel (whereas it does with a power lead boot).
So I am seeing an odd situation where more things crash when using the battery, but the battery icon never appears.
When I'm using mains power, there is only one system problem and the battery icon does appear in the top panel.
Anybody else seeing this?

---

### Post by dino99 on 2011-04-12
Some quite normal with bleeding hedge gnome3, not all packages fully compatible at time.

---

### Post by Quackers on 2011-04-12
I would agree, but only up to a point.
When using the battery for power I would expect it to be shown in the panel.
I could understand it if it didn't show up at all, but it does, when using AC power! That's odd.

---

### Post by gnomeuser on 2011-04-12
Apport doesn't work against PPA packages anyways and these would tend to be the largest source of bugs presently. You could just disable it for now.

see:
[https://wiki.kubuntu.org/Apport](https://wiki.kubuntu.org/Apport)

---

### Post by 23dornot23d on 2011-04-12
My laptops an Acer Aspire 7730ZG S 

I am not getting it on that ,,,,, and its constantly plugged in ......

---

### Post by bmbaker on 2011-04-14
my laptop is a Samsung R50 and quite old and i don't get them either !

---

### Post by nanouser on 2011-04-14
I had this problem after installing Gnome 3 from the Gnome 3 Team ppa on my new Acer Aspire One 522 Netbook. I forced a downgrade of "gnome-power-manager" and power management is working fine again.

---

