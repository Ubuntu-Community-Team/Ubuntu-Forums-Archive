---
title: "Totem Crashes"
date: 2010-12-31
forum: Multimedia Software
---

### Post by Sugi on 2010-12-31
> (totem:14383): Gtk-CRITICAL **: IA__gtk_tree_view_scroll_to_cell: assertion `tree_view->priv->tree != NULL' failed


I am running totem on Maverick, and it's streaming music from the network. It was working two days ago and now it's freezing [turns grey] and becomes unresponsive.  That's the only error I get from the terminal, but I don't think it's linked to the totem's freezes. Quick side note, the freezes doesn't cause all totem players to crash either.

Maverick x86
Totem 2.32.0

---

### Post by Sugi on 2011-01-01
I found the issue, for some reason I enabled my ufw thus causing massive issues with my network.

> sudo ufw disable

Input that command into the terminal and you're good to go.

Sugi

---

