---
title: "Xmms error on startup!"
date: 2007-07-14
forum: Multimedia &amp; Video
---

### Post by Alex&amp;Linux on 2007-07-14
Hey guys and gals!
Im a pretty big fan of internet radio, and xmms is a great vessel for it, however, there seems to be an error preventing its startup!

```
ajn@ajn-desktop:~$ xmms

Gtk-WARNING **: Unable to locate loadable module in module_path: "libbluecurve.so",

```

Ive looked in /usr/lib64/gtk-2.0/modules, and in /usr/lib/gtk-2.0/modules 
and found not this missing file!

Where has it run off to?

Ive also reinstalled it, and I have no other xmms packages save for xmms itself.
Interesting that a reinstall hasnt solved this particular issue....perhaps I need to purge it as well?

mmmm...

---

### Post by Alex&amp;Linux on 2007-07-14
Well, turns out that rebooting and launching the player before running compiz fusion was enough to get 'er up.

Ahora hay musica!

---

