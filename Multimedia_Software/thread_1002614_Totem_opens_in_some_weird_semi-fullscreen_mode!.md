---
title: "Totem opens in some weird semi-fullscreen mode!"
date: 2008-12-05
forum: Multimedia Software
---

### Post by isecore on 2008-12-05
I just noticed this five minutes ago, it hasn't happened before. Strangest thing.

Totem now opens in some weird half-fullscreen mode every time. It looks essentially like the normal mode, without window borders and with the full-screen controls overlaid on top. I haven't found a way to return it to normal.

Sure, it works as normal, and I can quit it from the menu. But it's rather annoying when it opens in this mode. Anyone know anything about it?

See attached screenshot for example of what it looks like. For some reason the full-screen controls disappear when I take the screenshot, doesn't matter if I hit printscreen or use scrot.

EDIT: I started it through a terminal just to see if it outputs some error message, and I noticed this:

```
** (totem:1482): CRITICAL **: bacon_video_widget_set_fullscreen: assertion `bvw != NULL' failed
```

Does it have anything to do with anything?

EDIT2: Never mind, I got it back to normal. I started it through commandline with the --fullscreen and that restored the borders for some reason, and I could resize it to a normal size. Now it's back to normal.

---

