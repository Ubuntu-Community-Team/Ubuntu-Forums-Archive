---
title: "specify xserver layout when starting gdm"
date: 2007-06-05
forum: Multimedia &amp; Video
---

### Post by soro2005 on 2007-06-05
Now I'm reasonably exhausted after an afternoon of trying to figure out how to set up my laptop for Dual Head. If anyone's interested: It's a Toshiba M35x-S349, and I found the solution at [http://filebox.vt.edu/users/jlido/linux/linux-m35x.html](http://filebox.vt.edu/users/jlido/linux/linux-m35x.html). I can use the xorg.conf that's up there, and it rocks. I hope the author is well and alive.

In any case: Now, I have two different ServerLayouts in my xorg.conf, and I can reference them when starting X with startx. Only that it seems I have to do that as su, meaning I end up in a gui as root. That, I don't want.

So, my question is: How do I start gdm so that it start X with a specific server layout?

Thanks!

---

