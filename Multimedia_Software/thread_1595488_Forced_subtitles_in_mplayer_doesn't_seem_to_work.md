---
title: "Forced subtitles in mplayer doesn't seem to work"
date: 2010-10-13
forum: Multimedia Software
---

### Post by thecapsaicinkid on 2010-10-13
Tested in both Karmic and Maverick.
```

mplayer dvd://1
```

hit 'j' key to cycle through subtitles until english subs are displayed

hit shift+f to enable 'forced subs only' during a scene with forced subtitles, subtitles dissapear, press it again to turn it off, subtitles re-appear.

or

```
mplayer dvd:// -sid 0 -enableforcedsubs
```

No subtitles appear. Tested the same disc on a standalone player and forced subs appear by default (this should be the default in players such as gnome-mplayer but that's an aside)

Can anyone else confirm this?

---

