---
title: "Laggy light themes"
date: 2010-08-31
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by kaldor on 2010-08-31
Why are the light themes so laggy when going through a dropdown menu? It's horrible :(

---

### Post by godhika on 2010-08-31
Quotes from Cimi (the theme author) from the canonical design blog
> I have reproduced the slower rendering speed of the menu. It’s not the menuitem being slow, but the nice glow around menu, because everytime you move the menuitem, the menu is going to be redrawn by Gtk+, and the glow requires CPU power. The only way to save performances is removing the glow effect, which is something I would like to avoid. and a short time later
> Performance boost for the menuitems will come next week. I have figured out a way to improve the algorithm 
So it will be better soon (hopefully)

---

### Post by kaldor on 2010-08-31
Makes sense. Hopefully it'll be sorted.

---

