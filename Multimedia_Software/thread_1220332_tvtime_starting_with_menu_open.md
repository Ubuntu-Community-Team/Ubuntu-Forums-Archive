---
title: "tvtime starting with menu open"
date: 2009-07-22
forum: Multimedia Software
---

### Post by ant_thomas on 2009-07-22
I've got a minimal ubuntu install with just an essential xorg install. No window manager.

I've got tvtime starting on boot and I have a few commands to sort settings and such. All this works a treat.

Anyway, I have one small but major problem. Whe tvtime starts the menu is showing. It only goes when pressing F1, Tab or Esc. This is a massive problem because the computer isn't going to have a keyboard or mouse.

So, does anyone know how to stop the menu showing on start? or, know of a way to execute F1, Tab or Esc when tvtime starts so it will close the menu?

---

### Post by waltersch on 2010-12-30
What I have experienced, is:

After installation, it seems to be intended that tvtime makes the first start with opened menu. You can immediately close the menu, and then all further starts are intended to have no menu open.

But: If you remove an installation of tvtime and then again install it (or a newer version of it), I have experienced that it ALWAYS starts with opened menu.

The way I got around it:
- Remove tvtime.
- delete the general settings: rm -R /etc/tvtime/
- From your home directory, delete the user-specific settings: rm -R .tvtime/
- Again install tvtime.
- At the 1st start, the menu is opened. Make the necessary settings and leave the menu.
All further starts come without menu.

I have gone that way only one time, thus I can't say whether it is a solution for all cases.
I won't touch it again, because I'm not sure I can repeat it.

So, perhaps this is a solution even if you don't have any keyboard or mouse. If not, you might have to use a keyboard only for the first start after re-installation. 

Good luck!

---

