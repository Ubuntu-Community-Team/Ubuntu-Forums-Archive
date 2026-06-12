---
title: "load different xorg configs with keyboard shortcut"
date: 2011-02-06
forum: Multimedia Software
---

### Post by walruspanzer on 2011-02-06
I have a laptop and external monitor. When I want to change the display configuration I have to open nvidia-settings, set the configuration, and apply the changes. Is there a way to bypass this and load different xorg configurations using keyboard shortcuts? I would be willing to settle for a command I can assign to a desktop shortcut to have the same effect if its possible. 
 
 
Ideally, I would like to be able to press ctrl-1 and have just the laptop screen, ctrl 2 for just external screen, and ctrl-3 for both. 
 
Does anyone have thoughts on this?

---

### Post by jamiehutber on 2011-12-01
bump? having the exact same problem

---

### Post by walruspanzer on 2011-12-01
I found a way using disper, a command line display switcher... Using native ubunutu you can assign disper -s and disper -S to new keyboard shortcuts right from the main menu under system>preferences. Switches between primary and secondary monitors. Once installed see disper --help for even more options. 

 [http://willem.engen.nl/projects/disper/](http://willem.engen.nl/projects/disper/)

---

### Post by jamiehutber on 2011-12-02
You don't by any chance have an nVidia graphics card do you?

I believe disper doesn't seem to work with ati :/

Been looking at Aranar... but it doesn't seem to work correctly.

---

