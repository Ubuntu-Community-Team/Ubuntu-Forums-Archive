---
title: "Rhythmbox takes unusually long time to load"
date: 2008-06-17
forum: Multimedia Software
---

### Post by snowball1288 on 2008-06-17
So it seems my Rhythmbox has developed an issue over the last few days.  my library is about 125GB, so it normally takes rhythmbox a few seconds to start up, but lately it will hang and become gray for upwards of 15 minutes while loading the library.  im not sure what has prompted this (no changes on my end, though ive been allowing it to do updates).  in any case, ive tried removing it, deleting the database XML file, deleting the entire rhythmbox folder under gnome2, and reinstalling several times but it hasnt helped.  I do, however, find that opening the database xml in gedit, waiting a few seconds, and then opening rhythmbox seems to help a lot.   

Ive tried running rhythmbox -d in the terminal and got a whole ton of these while it hangs and turns gray:  

(03:33:57) [0x80dc408] [rhythmdb_property_model_insert] rhythmdb-property-model.c:609: adding new property "Theme Song"
(03:33:57) [0x8840410] [queue_stat_uri] rhythmdb.c:2257: queueing stat for "file:///media/External/My%20CD's/Sam's%20Music/Snow%20Patrol/When%20It's%20All%20Over/Snow%20Patrol%20-%20An%20Olive%20Grove%20Facing%20The%20Sea.mp3"
(03:33:57) [0x80dc408] [rhythmdb_property_model_insert] rhythmdb-property-model.c:600: adding "Unknown": refcount 94
(03:33:58) [0x80dc408] [rb_entry_view_row_inserted_cb] rb-entry-view.c:1731: row added
(03:33:58) [0x8840410] [queue_stat_uri] rhythmdb.c:2257: queueing stat for "file:///media/External/My%20CD's/Jurassic%205%20-%20Quality%20Control/13%20-%20Jurassic%205%20-%20The%20Game.mp3"
(03:33:58) [0x80dc408] [rb_shell_clipboard_entries_changed_cb] rb-shell-clipboard.c:753: entryview changed
(03:33:58) [0x8840410] [queue_stat_uri] rhythmdb.c:2257: queueing stat for "file:///media/External/My%20CD's/Ash/Ash%20-%20Candy.mp3"
(03:33:58) [0x8840410] [queue_stat_uri] rhythmdb.c:2257: queueing stat for "file:///media/External/My%20CD's/Miscellaneous%20A-G/Dose%20of%20Adolescence%20-%20Plastic%20White%20Pens.mp3"


anyone have any ideas?  any help is much appreciated.

---

### Post by ruinairas on 2012-04-24
Rhythmbox has always been slow for me even using a SSD, not quite sure why but I just install Banshee.

---

