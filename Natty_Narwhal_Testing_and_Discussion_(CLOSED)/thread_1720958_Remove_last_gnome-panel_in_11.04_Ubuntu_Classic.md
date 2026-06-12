---
title: "Remove last gnome-panel in 11.04 Ubuntu Classic?"
date: 2011-04-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Zorgoth on 2011-04-03
The gconf key previously changed to permanently lose my last gnome-panel from all sessions no longer appears to exist, and I can't seem to make my session forget about the last gnome-panel, which I need to do in order to use the systray applet in cairo-dock.  Currently if I "killall gnome-panel" it immediately restarts.

---

### Post by lidex on 2011-04-03
Try editing the text files in ```
/usr/share/gnome-session/sessions
```

---

### Post by Zorgoth on 2011-04-03
That worked!  Thanks!  Before you did that I used the brute force method of uninstalling gnome-panel and telling the system to ignore all the related error boxes, but that was inconvenient as it broke alacarte.  Now everything works fine.  Thanks!

---

