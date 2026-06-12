---
title: "Syncing folders across my net work"
date: 2009-08-18
forum: Networking &amp; Wireless
---

### Post by b3n0 on 2009-08-18
Hey guys,

Not even sure if this is do-able. 

Here is the problem...
Using iTunes, I rip all of my newly bought CDs to my M$ Vista box.
Every once in a while (when I'm not feeling lazy), I set all the latest additions to copy across to my Ubuntu 9.04 Lappy. However, the process is a pain to manage (what do or don't I have etc), quite manual, slow, time consuming, and I don't do it anywhere near as often as I should; I'm often out and about looking for a song before remembering that I hadn’t added it. Not to mention, Vista is awful to network with. Talk about forcing the user to jump through hoops, often I just use a portable hard drive to do the updates.

This is what I'd like to have happen...
An ‘auto sync’, every time I turn my laptop on, it detects that it is part of my home network, and my desktop PC is on. If it could check for new additions or changes to the folder every time it turns on, it could mean just copying over 2 CDs, as opposed to 15. 

Any ideas? Can this even be done?

---

### Post by indigest on 2009-08-18
Sounds like you want to mount the networked folder and then use rsync to synchronize a local folder.  rsync is an awesome program which will only transfer files if there have been additions, changes, deletions, etc...

You might also check out grsync, which is a GUI frontend for rsync and is in the repositories.

---

