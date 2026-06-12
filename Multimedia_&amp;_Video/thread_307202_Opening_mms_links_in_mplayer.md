---
title: "Opening mms links in mplayer"
date: 2006-11-26
forum: Multimedia &amp; Video
---

### Post by anzas on 2006-11-26
i got a link on my desktop that opens an mms:// address, right now it opens it in totem and i would like to use mplayer instead, is there a way to do this?

---

### Post by ZiggyStardust on 2006-12-09
Hi anzas,
try to change the value for /desktop/gnome/url-handlers/mms/command in gconf-editor from **totem "%s"** to **mplayer "%s"**.

Ziggy.

---

