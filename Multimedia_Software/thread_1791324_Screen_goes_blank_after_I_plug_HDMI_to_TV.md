---
title: "Screen goes blank after I plug HDMI to TV"
date: 2011-06-26
forum: Multimedia Software
---

### Post by FelipeAragao on 2011-06-26
While I had my ubuntu 11.04 notebook hdmi output connected to my TV, I opened the monitors dialog and configured (don't ask me why) my laptop screen to be turned off. Now, everytime I connect the hdmi, my laptop screen goes blank and nothing appears on my TV. That's just a matter of deleting the automatic settings. Can you help me? Thanks!

EDIT: I logged in as root and could use dual screen without trouble. Looks like there's a file to be deleted in my home folder...

---

### Post by FelipeAragao on 2011-06-26
please help me! I'm still trying to get a solution for this.

---

### Post by FelipeAragao on 2011-06-26
HAHAHAH! Yeap! I solved it!

That's what I did: I found the file .config/monitors.xml running ```
find \. | grep monitor
``` and deleted it. Everything went back to normal! Gizz, I'm happy.

---

