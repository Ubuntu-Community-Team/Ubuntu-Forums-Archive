---
title: "What X Server Driver Does Radeon 9000 Use?"
date: 2007-08-09
forum: Multimedia &amp; Video
---

### Post by kh1116 on 2007-08-09
While trying to make Beryl work with my Radeon 9000, I accidently messed up the xorg.conf file. I tryed to recover the file with this command: ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
but when I do that, it asks me what driver I want to use, and I can't tell which driver to pick. So, what driver am I supposed to pick when my video card is a Radeon 9000? 
Thanks, Kevin

---

### Post by kh1116 on 2007-08-09
bump

---

### Post by pollywog on 2007-08-09
I've got a radeon 9600 that I recently installed and messed up my Xorg.conf file. There was some driver fglrx ,or something like that, that the automated setup installed and I couldn't get to work right. I went through the manual setup and chose "ATI" for driver, and everthing works OK now. -P.W.

---

### Post by kh1116 on 2007-08-09
I can't find ATI on the driver list, how do you do the manual configuration?

---

### Post by kh1116 on 2007-08-09
bump pls help

---

### Post by Raineer on 2007-08-09
If you just need to emergency recover, pick VESA (I think it's near the bottom)

---

### Post by kh1116 on 2007-08-12
too late i already reinstalled :) thanks for the help though!

---

