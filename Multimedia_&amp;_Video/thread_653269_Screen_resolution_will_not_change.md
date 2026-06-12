---
title: "Screen resolution will not change"
date: 2007-12-29
forum: Multimedia &amp; Video
---

### Post by runemaste644 on 2007-12-29
ok i have installed Ubuntu on another laptop, but its stuck on the default 800x600. Whenever i try in any way whatsoever to edit the screen resolution, no matter what, it crashes and i need to hard reboot. Switching virtual terminals never works because it crashes and never loads the command line. How do i get it to _not_ crash?

---

### Post by runemaste644 on 2007-12-29
Oh i know the answer to   the problem. Just run:
```
bump
```
:lolflag::lolflag::lolflag::lolflag::lolflag::lolflag::lolflag::lolflag:

---

### Post by taurus on 2007-12-29
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
What graphic card do you have on that laptop?

---

### Post by runemaste644 on 2007-12-30
ive already done that cmd. It crashes. I cant switch ttys because it also crashes.
I think its a savage graphics card.

---

### Post by runemaste644 on 2007-12-31
i reinstalled in regular graphics mode. Well, now we know sometimes its best to use UNsafe graphics mode! :lolflag:

---

