---
title: "Mixing Gnome 3 and Unity?"
date: 2011-03-27
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ExileAmongYou on 2011-03-27
I just had my first play around with Unity and Gnome 3 (I used the Fedora 15 alpha to look at Gnome 3). There's bits I like about both of them, but I think at the moment I'm leaning towards Unity, because what I really want is a DE that gives as much space as possible to my fullscreen apps, so I'm less likely to get distracted.

What I want to know is whether there's any way of combining things from Gnome 3 with Unity, e.g. that fancy new system of pop-up messages sliding down from the top of the application they're in, or those shiny new indicator menus Gnome 3 has. I'm not entirely clear on the whole Gnome/Gtk distinction, but am I right in thinking that some of this stuff would be linked to the Gtk version? Like, if I bumped my Gtk version in unity by using a ppa, I would get some of the new Gnome prettiness in Unity?

---

### Post by Merk42 on 2011-03-27
Some (all?) of what you like about GNOME 3 is actually GNOME Shell.
GNOME 3 (and 2 for that matter) have a variety of parts to them. GNOME Shell (the UI change) is one part, the shell.  Unity is also a shell, so I don't think you'll be able to run them simultaneously to get some aspects of GNOME Shell and aspects of Unity.

---

### Post by Harry33 on 2011-03-27
> **ExileAmongYou said:**
> I just had my first play around with Unity and Gnome 3 (I used the Fedora 15 alpha to look at Gnome 3). There's bits I like about both of them, but I think at the moment I'm leaning towards Unity, because what I really want is a DE that gives as much space as possible to my fullscreen apps, so I'm less likely to get distracted.

What I want to know is whether there's any way of combining things from Gnome 3 with Unity, e.g. that fancy new system of pop-up messages sliding down from the top of the application they're in, or those shiny new indicator menus Gnome 3 has. I'm not entirely clear on the whole Gnome/Gtk distinction, but am I right in thinking that some of this stuff would be linked to the Gtk version? Like, if I bumped my Gtk version in unity by using a ppa, I would get some of the new Gnome prettiness in Unity?

I am afraid you are mixing things up here quite a lot.

Gnome3 and its graphical shell, Gnome-Shell, depend on Gnu Tool Kit 3 (GTK+3) where Mutter is used as a window manager.

Canonical's Unity on the other hand is a GTK+2 based graphical shell, which is based on Compiz window manager.

These do not work together. You need to use in your Gnome session either one, but not both at the same time.

---

