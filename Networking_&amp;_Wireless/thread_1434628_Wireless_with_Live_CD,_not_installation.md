---
title: "Wireless with Live CD, not installation?"
date: 2010-03-20
forum: Networking &amp; Wireless
---

### Post by typofreak183 on 2010-03-20
I recently wiped my laptop running windows after trying out the Ubuntu 9.10 live CD. When I select the option on boot to "try ubuntu without changing your computer"
 or whatever, the Restricted Hardware Drivers window comes up announcing that my computer needs two different Broadcom packages to work properly with my wireless. I don't remember what packages they were, but now that I have actually installed Ubuntu, my wireless is completely dead. I'm using a wired connection right now, which works fine, but when I hope the Hardware Drivers app, I just get "there are no proprietary drivers in use on this system."

Why does this only work in the Live CD? Can I force Ubuntu to install the broadcom drivers?

---

### Post by 2hot6ft2 on 2010-03-20
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo apt-get update
```
type in your password when prompted and hit Enter it wont be displayed.
When it finishes check Hardware Drivers again.

---

### Post by typofreak183 on 2010-03-20
Will try. Hang on...

EDIT: If it makes any difference, the drivers I need are Broadcom STA and Broadcom B43.

---

### Post by typofreak183 on 2010-03-20
YAY! It worked!:D

Haha, I'm a total noob. Lesson learned: ALWAYS sudo apt-get update after a fresh ubuntu install. Always.

Thanks!

---

### Post by typofreak183 on 2010-03-20
How do I mark this thread as solved, BTW?

---

