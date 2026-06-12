---
title: "After upgrade to natty, screen smaller then monitor"
date: 2011-01-17
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Partan on 2011-01-17
Last week I upgraded from a new installed version of maverick to natty with: sudo update-manager -d.
So far everything is working as it should. But I have 1 major problem: the visible screen is smaller then the monitor. In other words, there is a black edge all around. Like I am looking at a 22" monitor instead a 24" as it really is. This effect is already visible when the splash screen shows. 
Futhermore, all the fonts in all the apps look a bit fuzzy.

Some data:
Ubuntu 11.04
Gnome 2.32.1
Kernel 2.6.37-12-generic
GCC 4.5.2 (x86_64-linux-gnu)
X-org 1.9.99.901 (1.10.0RC1)

Now I have no idea where to look and how to solve it.

---

### Post by cariboo on 2011-01-17
It would help if you told us what graphics adapter your system uses, since this is a graphics driver problem.

---

### Post by anders_c_ on 2011-01-17
You're probably stuck with the vesa driver which outputs a res your monitor doesn't support. Same thing happens for me during post and grub, but when the real drivers load up it uses the entire screen.

---

### Post by Partan on 2011-01-18
> **cariboo907 said:**
> It would help if you told us what graphics adapter your system uses, since this is a graphics driver problem.

Stupid of me, that is the part I forget.
My graphicscard is a Ati Radeaon HD 4650

---

### Post by Partan on 2011-01-18
> **cariboo907 said:**
> It would help if you told us what graphics adapter your system uses, since this is a graphics driver problem.

Stupid of me, that is the part I forget.
My graphicscard is a ATI Radeon HD 4650

---

### Post by anders_c_ on 2011-01-20
That card should be supported. Try booting up a daily-live, something might have gone wrong in the update process.

---

### Post by anders_c_ on 2011-01-20
That card should be supported. Try booting up a daily-live, something might have gone wrong in the update process.

---

