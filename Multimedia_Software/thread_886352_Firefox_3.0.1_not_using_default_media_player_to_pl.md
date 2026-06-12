---
title: "Firefox 3.0.1 not using default media player to play mp3"
date: 2008-08-11
forum: Multimedia Software
---

### Post by SSVegito888 on 2008-08-11
I am using Ubuntu Hardy 8.04 and Firefox 3.0.1.

Also, medibuntu and Ubuntu restricted packages are installed.

After clicking mp3 download url and clicking "RUN" inside of Firefox, Firefox does not open the associated media player to play the mp3.  Instead FF opens totem.


But when I download and save the mp3 to my hard drive, and double click the file in nautilus, it opens in the correct media player which is Amarok.

How can I correct this problem?


Thanks,

SSVegito888

---

### Post by cpetercarter on 2008-08-11
In Firefox, Edit > Applications - find the line "mp3 audio" and change the associated application from "Totem web-browser plugin" to the application you want.

---

### Post by SSVegito888 on 2008-08-11
I am sort of new to linux.


Where is amarok installed on the system?


Thanks,

SSVegito888

---

### Post by cpetercarter on 2008-08-12
Probably in /usr/bin/amarok. You can check by typing ```
whereis amarok
``` in a terminal.

---

### Post by SSVegito888 on 2008-08-13
Thanks for the command.

This will definitely come in handy!!!!



Thanks Again,

SSVegito888

---

