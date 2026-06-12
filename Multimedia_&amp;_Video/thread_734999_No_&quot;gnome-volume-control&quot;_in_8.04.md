---
title: "No &quot;gnome-volume-control&quot; in 8.04"
date: 2008-03-25
forum: Multimedia &amp; Video
---

### Post by RossAndGarfunkel on 2008-03-25
I just upgraded to the latest beta of 8.04 last night, and so far I haven't been able to get audio working at all. It has always worked fine for me on 7.10. I am on an Acer Aspire 5600 laptop, using an Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02). If I double-click on the volume control, it says

"Failed to start Volume Control: Failed to execute child process "gnome-volume-control" (No such file or directory)"

Do I need a reinstall? Or is there a simpler solution?

---

### Post by RossAndGarfunkel on 2008-03-25
any ideas?

---

### Post by theKay on 2008-05-07
sudo apt-get install gnome-media 

It fixed it for me.

---

