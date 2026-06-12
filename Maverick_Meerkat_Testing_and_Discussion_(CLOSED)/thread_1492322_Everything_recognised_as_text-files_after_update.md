---
title: "Everything recognised as text-files after update"
date: 2010-05-24
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by moviemaniac on 2010-05-24
Hi guys,

I've got a very weird problem - since today's updates (and reverting libgtk+ back to the old version) Ubuntu now recognizes _every_ file as a text file and wants to open it with gedit. Anyone having the same issue or a hint on how to fix this?

//edit: it only seems to affect nautilus, Thunar and Dolphin work just fine...

Thanks,
mm

---

### Post by moviemaniac on 2010-05-24
purging most of ./local/share (left a few files I thought were unrelated but deleted most of the non-essentiall stuff) fixed it.

---

### Post by moviemaniac on 2010-05-26
Okay, this is not solved.

I booted into KDE this morning to check it out (I one installed it alongside Gnome during the lucid cycle but never really used it) and when I returned to gnome the MIME-associations were messed up again.
I guess this has something to do with KDE starting to use the shared-mime-thingy which messes things up for systems using both GNOME and KDE. My fix so far: I completely removed KDE and everything associated with it as I don't use it anyway (safe for a few programs I also use in Gnome).

---

### Post by dino99 on 2010-05-26
same issue with FF opening some urls (a few)

---

