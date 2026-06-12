---
title: "Monitor resolution help"
date: 2009-07-26
forum: Multimedia Software
---

### Post by boba52 on 2009-07-26
Hello:
Can anyone help me with setting my resolution higher it only lets me go as high as 800x600 at 60 hrtz. this is bullcrap as I have a diamond pro which will do far more than that . I don't want to reload the entire os again as I had too many troubles with the disk in the first place, I know c and c++ and some other programming languages but don't know linux shell commands as yet ,new but will learn them as soon as possible.

Please guide me through this and if I can help you with something in return I will!

Thanks very much 

Bob A

---

### Post by 67GTA on 2009-07-26
Not sure what a diamond pro is. What graphics card do you have? Post the output of ```
lspci
``` from a terminal.

---

### Post by Yellow Pasque on 2009-07-26
Post your /var/log/Xorg.0.log file. I've seen several case of Xorg failing to detect the virtual screen size, and setting it to 800x600, limiting your resolution.

---

