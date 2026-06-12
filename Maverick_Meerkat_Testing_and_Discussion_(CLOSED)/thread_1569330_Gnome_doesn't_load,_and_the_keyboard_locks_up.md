---
title: "Gnome doesn't load, and the keyboard locks up?"
date: 2010-09-06
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by NCLI on 2010-09-06
When trying to install Maverick on my Desktop, I ran into quite a few issues. First off, when using the live cd and selecting "Install Ubuntu," the installer didn't appear. I then tried to use the other option "Try Ubuntu without installing," but that simply left me staring at the plymouth screen. If seemed like everything loaded, just in the background. Also, the keyboard locked up, and even the *lock keys didn't work, unless I used "ctrl+sysrq+r". 

Finally, I successfully installed it with the alternative cd, but now I'm again stuck with a locked keyboard and a cursor, only this time it's not during plymouth, but just after having logged in using GDM! Only the cursor and the... interesting wallpaper are on the screen; no icons, no panels, no nothing.

I was able to use ctrl+alt+F1 to get to a TTY before logging in, and installed all available updates. Didn't help.

Anyone else experiencing this??

---

### Post by ranch hand on 2010-09-06
Can you log into any other session like failsafe gnome?

---

### Post by NCLI on 2010-09-07
Nope, and not Unity either. I'm beginning to think this is a GDM bug...

EDIT: I've reported [the bug]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/632231").

---

### Post by VMC on 2010-09-07
> **NCLI said:**
> Nope, and not Unity either. I'm beginning to think this is a GDM bug...

EDIT: I've reported [the bug]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/632231").

Isn't Unity mainly for laptops? You mentioned you tried this on your desktop. at any rate, what hadward is your desktop, cpu,ram, video - ati/nvidia/intel?

---

