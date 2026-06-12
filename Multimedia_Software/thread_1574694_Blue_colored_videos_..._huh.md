---
title: "Blue colored videos ... huh?"
date: 2010-09-14
forum: Multimedia Software
---

### Post by ed-koala on 2010-09-14
My PC just started acting very, very strange.  The graphics did some sort of hiccup, and I had to restart to fix my screen.

Now though all my videos play with strange colors.  People are blue, etc. Very odd looking.  I tried reinstalling the drivers, but nothing has helped.  Both Totem and VLC are the same, so it's not the program itself.  My icons and other programs have the correct colors, it's just videos that are all mixed up.

Any ideas what's wrong, or how to fix?

---

### Post by mc4man on 2010-09-14
Try opening Totem -> edit -> preferences -> Display and move either the saturation  or the hue slider all the way to one side and then back to middle.

---

### Post by ed-koala on 2010-09-14
That sorta did it.  I have to have hue all the way to the right.  Is this normal?

---

### Post by mc4man on 2010-09-14
> I have to have hue all the way to the right
you should be able to now move back to 'normal' - try moving it back and forth, then to middle. (maybe close and reopen totem, after moving back you could then click on 'reset to defaults' to center the slider

Otherwise there is a gconf-editor setting, though the values are not intuitive

Edit; I've only had this happen once or twice a long time ago, part of a nvidia bug. Those settings actually have no effect here, it was more the act of moving the sliders that fixed things. (I could move them all to 0 with no change, color is controlled in nvidia-settings

---

### Post by ed-koala on 2010-09-14
Definately a video driver bug of some sort.  Right before that my display suddenly went part offscreen and some of it was garbled.  Some sort of hiccup occurred.

Well, it's fixed now so no biggie.  Thanks!

---

