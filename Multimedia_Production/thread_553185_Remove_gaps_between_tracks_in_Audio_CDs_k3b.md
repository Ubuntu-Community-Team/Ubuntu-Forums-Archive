---
title: "Remove gaps between tracks in Audio CDs k3b"
date: 2007-09-17
forum: Multimedia Production
---

### Post by Eithel on 2007-09-17
Hi guys, I'm searching a simple way to remove the gaps between tracks in Audio CDs in the k3b program. I've found, on the net, some guides that says:
[I]"Should you want to change the default two second silent gap between tracks, right click on a track
and select Properties. In the Audio Track Properties window that opens, click on Options and raise or lower
the Pregap value"[/I]

But in my Audio Track Properties window there is a Post gap option but i don't have any Pregap value. I tried to set Postgap value to 0, and burn cd in disk-at-once (DAO) mode, but my Cd has always two seconds silent gap !

Can someone help me to remove this gap ??
It's very annoying on live tracks :(

---

### Post by tofudrifter on 2008-03-12
bump

i've got almost the same problem except it removes the 2 second gap, but there's a crackle 2 seconds before the end of every track

---

### Post by eye208 on 2008-03-12
For gapless live recordings try gcdmaster. It's the "official" GUI front end of cdrdao. It lets you load live recordings in one piece, set the track index markers anywhere and burn the result in DAO mode. There will be no crackles since the tracks need not be split up into separate files before burning.

---

