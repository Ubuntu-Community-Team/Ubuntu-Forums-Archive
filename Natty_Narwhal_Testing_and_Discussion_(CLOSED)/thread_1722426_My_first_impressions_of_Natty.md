---
title: "My first impressions of Natty"
date: 2011-04-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ZarathustraDK on 2011-04-05
So, I just installed this evening, and it was kind of not without its share  of problems.

Luckily it wasn't due to Natty being a borked pig, but rather a mischievous usb-stick which put me in a world of hurt.

How best to explain it? Well, stuff got messed up during install, the usb would hang, causing some packages to become faulty. It's not the first time I've had these problems (on other computers too, with other versions of Ubuntu), and generally 2 things always seem to be the case: 1. it's always a USB-flashdrive, and 2. "burning" the image to the usb (or installing for that matter) while it's loaded in a front-slot (slow usb 1.0 port) instead of the backside (usb 2.0).

Why does it happen? Is the usb-stick's cells getting killed and messing up the checksums or something? The surefire way to make the usb-installer work seems to be to repartition the stick with same fat32 filesystem before burning the stick with the "make usb startup disk"-application.

Have anybody else had this problem? The solution is pretty simple, but not quite obvious. I always forget the above between installs, and start mucking around in console-mode trying to fix the unfixable (well to me at least) thinking it's some hardware problem or a missing package. It can leave a scar on those unwilling to persevere, just sayin' ;)

Other than that, my only gripe so far is that the Unity-bar disappears every time I use it to open a window. The window appears too close to the bar, and the bar autohides. We're talking about a 1-2 pixel-distance further to the right before it wouldn't do this.

Otherwise I'm a happy camper so far. Graphics are nice and snappy, and compositing is finally starting to look like it's meant to be there. Cheers.

---

### Post by el_koraco on 2011-04-05
move the mouse to the top left corner and it will appear again. or install ccsm, go to the unity plugin and set the launcher to always be visible. dodge windows is the default.

---

### Post by ZarathustraDK on 2011-04-06
> **el_koraco said:**
> move the mouse to the top left corner and it will appear again. or install ccsm, go to the unity plugin and set the launcher to always be visible. dodge windows is the default.

Dodge is the default. Dodge while active doesn't help either, as the windows that appear are active. Always visible is also a no-go, I do want it to disappear when I don't use it. Resizing the icons doesn't help either, the windows just creep further left overstepping the autohide-boundary. What I'm trying to accomplish is getting the windows to spawn a teency weency bit more to the right so they don't trigger autohide when the user might want to open up more programs in a sequence (for instance, open up 3 different disk-drives for copying back and forth.

---

