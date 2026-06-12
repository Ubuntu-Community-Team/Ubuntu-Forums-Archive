---
title: "help with wireless"
date: 2008-12-09
forum: Networking &amp; Wireless
---

### Post by Dawei87 on 2008-12-09
i am new to kubuntu and i am trying to get my wireless set up. i did it once on ubuntu and i think i can do it the same way, but im not sure how to run the commands. i am trying to edit the file blacklist under modprobe.d, but the command gksudo gedit no longer works. is there an equivalent command in kubuntu?

---

### Post by asker on 2008-12-09
What does it say when you run that command?
First try running gksudo kate, or gksudo nano modprobe.d
 
(You could also try running sudo kate modprobe.d or sudo nano in a terminal)

---

### Post by Dawei87 on 2008-12-09
thank you! gksudo kate worked. when i typed in gksudo gedit absolutely nothing would happen. it didnt bring up any lines in the terminal or any windows at all. is there a reason that wouldnt work?

---

### Post by gnusci on 2008-12-09
Well, **Ubuntu** use **GNOME** desktop. **gedit** is a **GNOME** package:

[http://projects.gnome.org/gedit/](http://projects.gnome.org/gedit/)

and you installed **kubuntu** that use **KDE**, so it seem that there is not **gedit** installed by default, but **kate** an **KDE** based editor:

[http://kate-editor.org/](http://kate-editor.org/)

---

