---
title: "Rhythmbox does not open at first clic"
date: 2010-02-06
forum: Multimedia Software
---

### Post by rafeviper on 2010-02-06
Hi,

Since yesterday I'm having a little problem with Rhythmbox: I have to click twice on the Rhythmbox launcher to get it open, I can't get into the Properties of any file, it doesn't show the Desktop Art plugin... so far.

When I try to run it from the terminal, it shows this:



rafeviper@rafeviper-laptop:~$ rhythmbox

** (rhythmbox:1323): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:1323): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

(rhythmbox:1323): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(rhythmbox:1323): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(rhythmbox:1323): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(rhythmbox:1323): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(rhythmbox:1323): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated



Comparing it to a friend, it's missing the next line:


WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect


Any ideas how could I solve this?

Peace!


P.S: Forget about it, it was running as it were a widget (I activate it on Compiz).  Sorry.

Solver =D

---

