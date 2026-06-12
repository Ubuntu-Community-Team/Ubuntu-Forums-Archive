---
title: "Rhythmbox wont open .pls files properly"
date: 2011-01-09
forum: Multimedia Software
---

### Post by nixwit on 2011-01-09
Apparently even when I tell firefox to use /usr/bin/rhythmbox to play .pls files it segfaults. I've tried a number of searches I've got gstreamer installed (according to posts this is needed). Is there a rhythmbox script wrapper to push the uri to rhythmbox in the proper format? A few of the threads had rhythombox-client listed although they were older and after reading them they were not resolved at that time. Anyone know how to fix this? Rhythmbox will play mp3s tho and I can paste the url into the add radio stream dialog in rhythmbox although sadly this often screws up the title and just leaves the url as its title.

---

### Post by mc4man on 2011-01-09
With the latest rb ver. (13.2) and probably latest totem-pl-parser (as seen in natty (11.04) rb will no longer segfault on a .pls

After that it still goes downhill - 

Rb will open but not start playback. What will happen is all the entries in the .pls will be added to the 'radio' list and can be manually started from there.
Unfortunately (maybe), these become permanent entries and will possibly get a bit messy if you open a number of .pls's in rb, ie, you may end up w/ hundreds of entries.

(though you could remove unneeded dups

Other option is to use just about any other player.

Old bug report, w/ some new 
[https://bugzilla.gnome.org/show_bug.cgi?id=383328](https://bugzilla.gnome.org/show_bug.cgi?id=383328)

---

