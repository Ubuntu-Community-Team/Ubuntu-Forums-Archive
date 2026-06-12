---
title: "totem frameless"
date: 2008-02-10
forum: Multimedia &amp; Video
---

### Post by deleonjavier on 2008-02-10
ok so i've been messing with my totem to alter to its best. but recently i guess i've must have done something that it didn't like. when i open it up under my username it shows up with no frames (fullscreen). I put totem in terminal it output the following:


** (totem:7019): CRITICAL **: bacon_video_widget_set_fullscreen: assertion `bvw != NULL' failed

** (totem:7019): CRITICAL **: bacon_video_widget_set_show_cursor: assertion `bvw != NULL' failed
sh: jackd: not found


What does this mean. I've removed it completely from the system and reinstalled but i get the same results, the fullscreen. I've removed and installed, reinstalled. Everything i could imagine. Any help?

---

### Post by deleonjavier on 2008-02-10
ok so I disabled compiz and then enabled them back again. totem works now but I haven't restarted my computer, we'll see what happens from that point. I know that to choose the totem video output its system>preferences>multimedia systems selector. Right now, its selected on No Xv which is good for viewing with compiz effects but not for viewing totem video in fullscreen because then it becomes really grainy. But X11/XShm/Xv is really good for fullscreen but horrible for compiz effects because it doesnt work with moving windows.. sorry for the length of the post  and thanks for all those who read.  hopefully once i restart it will still work.

---

