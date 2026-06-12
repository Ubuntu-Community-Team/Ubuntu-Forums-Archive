---
title: "Compiz upgrade &gt; Menus too wobbly"
date: 2006-09-05
forum: Multimedia &amp; Video
---

### Post by Clark Nova on 2006-09-05
I installed the latest upgrades for Compiz this morning but now I think the menus are a bit too wobbly and I want to change them if I can . Can anybody help me with this?

Thanks:)

---

### Post by rob martin on 2006-09-05
Compiz no longer uses gconf to handle the plugins (said to remove a gnome dependency, lot of wheels being reinvented here IYAM) it now uses csm to handle plugins.  To "fix" your wobbly menus open a terminal and run csm.  The  setting you wish to change is under wobbly windows (left menu) and Simple Strings (tab menu) Change Map effect from Shiver to None and menus back to "normal" until compiz changes again ;)

---

