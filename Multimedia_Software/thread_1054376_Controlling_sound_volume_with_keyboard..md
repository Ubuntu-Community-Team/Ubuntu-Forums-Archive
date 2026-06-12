---
title: "Controlling sound volume with keyboard."
date: 2009-01-29
forum: Multimedia Software
---

### Post by PoopLoops on 2009-01-29
Yes, it works for me, but my specific question is how do I adjust how big the steps are?  I want to make them smaller, because now it's either too loud or too quiet when I hit up or down once.

Thanks.

---

### Post by engineuity on 2009-01-29
I had the same issue. You can adjust this through the gconf-editor.

```
$ gconf-editor
```

Select apps -> gnome_settings_daemon

You can then right click on the "volume_step" and change the key. I changed mine to 3 from 6. Hope this helps.

---

### Post by PoopLoops on 2009-01-29
Yes it does!  Thank you. :D

---

