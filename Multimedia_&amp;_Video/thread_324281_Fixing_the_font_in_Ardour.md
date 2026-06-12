---
title: "Fixing the font in Ardour"
date: 2006-12-23
forum: Multimedia &amp; Video
---

### Post by Hanj on 2006-12-23
For some reason, the font in Ardour looks really ugly on my machine, and on some places it's barely readable. See the attached file. Judging by screenshots such as [this]("http://www.linuxjournal.com/articles/lj/0131/7796/7796f1.png"), it's possible to at least make it readable. I've looked everywhere for a fix, but nothing so far.

---

### Post by bramvandijk on 2007-01-15
The thing with Ardour is that it uses GTK1, which is really ugly. However, Ardour 2.0 should be completed soon, and this uses GTK2 and looks a lot better. Hopefully this will be in time for Feisty.

---

### Post by sjara on 2007-01-23
> **Hanj said:**
> For some reason, the font in Ardour looks really ugly on my machine...

Try changing the font in /etc/ardour/ardour_ui.rc
It fixed it in mine when I changed from Helvetica to other fonts (and even when a changed it to a name that does not correspond to an installed font).

---

