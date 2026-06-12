---
title: "Maya 8.5 causes system to hang"
date: 2007-10-15
forum: Multimedia &amp; Video
---

### Post by Sirron on 2007-10-15
I have installed Maya 8.5 on my laptop, in the same way as on my desktop (converted the packages with alien, following a guide). It works fairly well on my desktop, with only a few menu glitches (because it uses motif, why?!).

But on my laptop it completely hangs if I try to change the views. I can create and modify models... just not change the view panel layout. If I do, the CPU goes to 100% usage (I assume, given the way the fan goes to max speed), and nothing happens. The area where the view panels would occupy goes grey, as if there's nothing there, and although the mouse pointer moves, nothing can be clicked. I have to manually restart the computer, as x will not restart with ctrl alt backspace. Also, I cannot switch to a terminal with ctrl alt and F1/2/whatever.

I reckon it must be to do with motif. But I don't know what to do about it... can anyone help please?

---

### Post by Ph0N37Ic5 on 2008-03-26
I have the same problem running maya 8.0 on U7.10, it seems to be a problem with the HUD menus, the context menus and the menu for the shelf.

Bringing up any of these hangs the system or parts of the system. 
Sometimes it will hang everything but maya and the ability to change to the console, changing to another program when the system is in this state will hang the whole system and nothing but a hard reboot will help.
If you can get into the console you can 'killall maya.bin' and that will unfreeze the system.

Everything else seems to work as normal.

---

