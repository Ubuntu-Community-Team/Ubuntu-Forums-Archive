---
title: "Can't load any svg files"
date: 2008-10-29
forum: Multimedia Software
---

### Post by phorgan1 on 2008-10-29
In spite of having libsvgr I can't open any svg files with anything.  Using Ibex.  For example:
> eog /usr/share/gnome-control-center/pixmaps/visual-effects_custom.svg 
Could not load image 'visual-effects_custom.svg'.
Unrecognized image file format

Can anyone help?  I've tried everything.

Patrick

---

### Post by lemming465 on 2008-10-30
Did *everything* include ```
sudo apt-get update; sudo apt-get upgrade --fix-broken
```
That has sometimes helped me in the past.  Was your ibex install fresh, or an upgrade from heron?

On my system (wubi install of 8.04 upgraded to 8.10rc) your eog command works OK.  I note in passing that I don't have a libsvgr, though I do have a librsvg, which *dpkg -S* says belongs to *librsvg2-2*, which *aptitude why* says is a dependency of *python-gnome2-desktop*.  *ldd /usr/bin/eog* didn't depend on any libraries with svg in their names; I'm not sure where its svg support is hiding.

---

