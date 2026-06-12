---
title: "Rhythmbox crash on launch."
date: 2013-03-20
forum: Multimedia Software
---

### Post by Pufftones on 2013-03-20
Hey, so Rhythmbox has started crashing when I launch it.  Upon initial investigation, I thought it was related to it upgrading to an unstable version from the WebupD8Team which was a software source I added so that I could use the PPA for mounting an Android phone.  I forced it in Synaptic to downgrade the official Ubuntu version and it still does the same thing, when I launch from the terminal I get this ...

(rhythmbox:3089): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:2:19: Theming engine 'adwaita' not found


(rhythmbox:3089): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:4031:64: Error opening file: No such file or directory


** (rhythmbox:3089): WARNING **: GObject.get_data() and set_data() are deprecated. Use normal Python attributes instead


(rhythmbox:3089): Gtk-WARNING **: Inserting action group 'WebMenuActionGroup' into UI manager which already has a group with this name




(rhythmbox:3089): Gtk-WARNING **: Inserting action group 'WebMenuContextActionGroup' into UI manager which already has a group with this name




(rhythmbox:3089): Gtk-CRITICAL **: gtk_box_pack: assertion `gtk_widget_get_parent (child) == NULL' failed


(rhythmbox:3089): Rhythmbox-WARNING **: Could not open device /dev/radio0
**
RhythmDB:ERROR:rhythmdb-tree.c:1517:remove_child: assertion failed: (g_hash_table_remove (parent->children, data))
Unable to open ~/.mtpz-data for reading, MTPZ disabled.Aborted (core dumped)


It opens and as soon as it loads my entire music library is when it crashes and it gives me that final output starting at "RhythmDB:ERROR:rhythmdb-tree..." as soon as it crashes.  If anyone knows what it is asking me for and has any advice on how to go about solving this, I would greatly appreciate any ideas/advice.  Thanks.

Pufftones

---

### Post by Pufftones on 2013-03-20
Ok, I figured it out, I did a terminal search for Rhythmdb, deleted the only file that it found which was just a file of everything that I had in the music library.  Had to add all my music back in but it seems to be working just fine now.

---

### Post by Adrian Challinor on 2013-03-28
Many thanks - Solved my issue

---

