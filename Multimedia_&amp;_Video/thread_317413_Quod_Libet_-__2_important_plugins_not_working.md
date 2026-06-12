---
title: "Quod Libet -  2 important plugins not working"
date: 2006-12-12
forum: Multimedia &amp; Video
---

### Post by robenroute on 2006-12-12
Hi there,

I've installed hugmenot's Quod Libet .deb packages for Edgy (version 24.1, although in QL's About window it says it's version 25.0....). The whole install went fine, apart from the fact that when selecting plugins from the music menu, and then clicking the Errors button, there's a report of 3 plugins (of which 2 rather important ones) not working:


```
Traceback (most recent call last):
  File "/usr/share/quodlibet/plugins/songsmenu/brainz.py", line 4, in ?
    import musicbrainz, os, gtk, re
ImportError: No module named musicbrainz
```

The same for the CDDB and submitlastfm plugins. Someone out there who knows how to solve this? Thanks a lot in advance.

Rob

---

