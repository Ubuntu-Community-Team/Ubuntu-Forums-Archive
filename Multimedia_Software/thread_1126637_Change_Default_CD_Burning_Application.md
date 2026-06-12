---
title: "Change Default CD Burning Application"
date: 2009-04-15
forum: Multimedia Software
---

### Post by SketchyClown on 2009-04-15
Been doing some Googlin' and haven't had much luck.

I'm not a fan of Brasero, and since I use Gnome, I'm not interested in K3B.

The application I love using is **GnomeBaker** as it has yet to ever make a coaster for me.

I know it is apparently no longer supported, but it is a great program.

I would like to know if anyone here knows how to change the default CD burning application. When I insert a blank disc, the dialog pops up asking what program should be used but it says **no programs installed** even though GnomeBaker is.

I don't see this being rocket science and maybe I'm missing some file that's a piece of the puzzle, but right now, I am stumped.

Anyone?

---

### Post by Bakon Jarser on 2009-04-15
Should be in this file

gksudo gedit /etc/gnome/defaults.list

search for:

x-content/blank

I would make a backup copy of this file before editing it.

---

### Post by SketchyClown on 2009-04-15
> **Bakon Jarser said:**
> Should be in this file

gksudo gedit /etc/gnome/defaults.list

search for:

x-content/blank

I would make a backup copy of this file before editing it.

Thanks mister! I have managed to get GnomeBaker to launch now upon CD insertion.

:popcorn:

---

