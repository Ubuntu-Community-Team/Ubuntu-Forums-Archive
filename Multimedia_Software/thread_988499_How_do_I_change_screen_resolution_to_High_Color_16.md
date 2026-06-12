---
title: "How do I change screen resolution to High Color 16 bit?"
date: 2008-11-20
forum: Multimedia Software
---

### Post by Elliander on 2008-11-20
I am trying to run a game, Creatures 3, which requires that the screen resolution be set to High Color 16 bit. Problem is, the GUI screen resolution has neither option.

I tried the command:

sudo gedit /etc/X11/xorg.conf

Changed 24 to 16. (under default depth) and saved the change. But the game still won't run.

I don't know if it is because I didn't actually change it to 16 bit, or if I still need to change to "High Color" since both are required.

(It would be nice if Ubuntu included such along side the screen resolution in a future update.)

---

### Post by RtVD on 2008-11-21
as far as I can tell... you can't really

all the xorg stuff for 8.10 is probed on startup each time.


Gnomes removal of options (screensaver, cpu scaling settings, graphics options, reconfigure no longer doing anything other than the keyboard..) is driving me away from ubuntu, I think I'll wipe this box in a day or so and install Xubuntu or Kubuntu, as they will let me use my laptop.

-RtVD

---

