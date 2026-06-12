---
title: "ssa/*** subs crash"
date: 2012-02-04
forum: Multimedia Software
---

### Post by shmibs on 2012-02-04
recently, nearly every matroska file i play that uses one of these two subtitle formats and attached fonts crashes with this message as soon as anything is supposed to be displayed:
malloc.c:3574: mremap_chunk: Assertion `((size + offset) & (mp_.pagesize-1)) == 0' failed.
Aborted

this happens under totem and vlc. parole displays text, but in an ugly font, and gnome-mplayer just freezes.
it doesn't happen with every file either. a few that use common fonts, like Tahoma, will display properly. it didn't happen at all a little while ago, though, which is why i'm puzzled about what happened.

---

