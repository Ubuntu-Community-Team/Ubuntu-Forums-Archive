---
title: "RC-LiveCD aint working with my gfx-card and xforcevesa aint working either"
date: 2010-10-06
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Npl on 2010-10-06
Already had annoying problems with 10.04, but it only got worse with 10.10 (release canditate).
The LiveCD apparently uses a driver for my Geforce240 (noveau) that displays only noise, cant switch to textconsoles or restar X (Crtl+Alt keycombos).
Trying to boot into VESA-Mode by appending xforcevesa to the bootparameters aint working either.

Nice going!

---

### Post by cariboo on 2010-10-06
Try setting nomodest from the menu screen. Press any key when you see the initial screen to get to the menu, then press F6 and select nomodeset (it's the same as safe graphics mode), then press return. You should now boot to a desktop.

BTW Ctrl-Alt-Backspace was depreciated a couple of releases ago.

---

### Post by Npl on 2010-10-06
> **cariboo907 said:**
> Try setting nomodest from the menu screen. Press any key when you see the initial screen to get to the menu, then press F6 and select nomodeset (it's the same as safe graphics mode), then press return. You should now boot to a desktop.That did the trick, thanks. Wish I could just tell to ignore the nouveau driver, just plain aint working for me in 10.10 or 10.04. Shouldnt be the default in its current state, nv driver atleast works.
> **cariboo907 said:**
> BTW Ctrl-Alt-Backspace was depreciated a couple of releases ago.Ahh, forgot about that. Changing sessions (Ctrl-Alt-F1) dint work either but thats probably because modesetting is now in the kernel.

---

