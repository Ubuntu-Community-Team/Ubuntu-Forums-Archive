---
title: "Upgrade to Lucid (10.04) Menu Items disappear"
date: 2010-05-21
forum: Mythbuntu
---

### Post by scovel on 2010-05-21
I upgraded my backend and frontend to 10.04 tonight (from 9.10).  Went smooth.  brought the machines back up and the frontend looked strange.  When I move the selection from menu item to menu item, the one that is selected disappears completely.  I was using Project Grayham.  I also tried blootube, neon,  and Mythcenter.  The only one that worked right was Mythcenter.

Epia SP13000, Nvidia 9400 GT

Anyone have the issue?  Is there a workaround?

---

### Post by nickrout on 2010-05-21
Most, if not all of those themes are not 0.23 compatible themes. 

Try deleting your theme cache, in ~/.mythtv for the user running mythfrontend.

Choose something like arclight or one of the other mythui compatible themes.

---

### Post by scovel on 2010-05-21
Tried to figure out which themes are not compatible. I found a commit that removed a bunch of themes from .23:
 
themes/ProjectGrayhem (deleted) 
themes/ProjectGrayhem-wide (deleted) 
themes/blootube (deleted) 
themes/blootube-wide (deleted) 
themes/blootubelite-wide (deleted) 
themes/neon-wide (deleted) 
 
Just an FYI for Googlers.
 
Seems to me most of what are left are pretty heavy themes for my poor Epia to deal with.

---

