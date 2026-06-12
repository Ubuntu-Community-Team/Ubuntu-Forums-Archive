---
title: "[SOLVED] Terminal window hangs during Sun licensing confirmation"
date: 2008-11-27
forum: Multimedia Software
---

### Post by Rulls on 2008-11-27
As I go through the system update procedure described in "Comprehensive Multimedia & Video HowTo" (terminal window method), the process gets hung up at the point where the Sun Java license agreement is displayed, awaiting user acceptance.

I may be missing something simple, or else there is no way out of this license agreement panel.  I can page up and down through the text of the agreement, and the escape key briefly clears the license agreement overlay and shows the waiting package unpacking step, but no other key or combination or mouse-click seems to activate the OK shown at the bottom of the screen.

Any way out of this?  What am I missing?

Thanks in advance for any assistance.

(Intrepid Ibex, 64-bit)

---

### Post by sisco311 on 2008-11-27
Try the Tab key and/or arrow keys to highlight the option,  Space and/or Enter to select it.

---

### Post by Joeb454 on 2008-11-27
> **sisco311 said:**
> Try the Tab key and/or arrow keys to highlight the option,  Space and/or Enter to select it.

If I remember correctly you have to use the right arrow key to select the "yes" option (or something like that).

It's certainly awkward :p

---

### Post by Rulls on 2008-11-27
Holy crap!  That works!  I was sweating the prospect of interrupting this (very large) update and dealing with the resulting mess.  Thanks very much for your quick and correct assistance.

---

### Post by sisco311 on 2008-11-27
> **Joeb454 said:**
> If I remember correctly you have to use the right arrow key to select the "yes" option (or something like that).

It's certainly awkward :p

If you find it awkward you can change the interface:
```
sudo dpkg-reconfigure debconf
```

dialog (default)
readline (text based)
gnome & kde (GUI)
editor (default editor)
noninteractive

---

