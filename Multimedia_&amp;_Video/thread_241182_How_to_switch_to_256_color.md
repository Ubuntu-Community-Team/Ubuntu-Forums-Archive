---
title: "How to switch to 256 color"
date: 2006-08-22
forum: Multimedia &amp; Video
---

### Post by lnxnewbie on 2006-08-22
Is there a way to switch to 256 color (8bit depth) mode?
I cannot locate that "display option" in none of the menu.
Regards,

---

### Post by tseliot on 2006-08-22
Sure.

Type:
```
sudo nano -w /etc/X11/xorg.conf
```
get to the Section "Screen" and set the "DefaultDepth"    to 8

---

### Post by lnxnewbie on 2006-08-22
Thank you very much. Works like a charm!

---

