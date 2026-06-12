---
title: "weird problem with dual-monitors"
date: 2007-11-15
forum: Multimedia &amp; Video
---

### Post by blinger on 2007-11-15
I'm wanting to setup dual monitors.. im a newb at ubuntu so i'm not sure exactly where im going wrong. I followed a guide on these forums that had me copy/paste some info into my xorg.conf file.. after doing this and restarting it knocked my LCD Gateway FPD1520 off. I reverted the changes and the monitor still will not come on. 

First, copy/pasting the info into my xorg.conf and rebooting didnt give me 1 large desktop, actually - it didnt do anything! second, the screen still works up until after i login. it displays the login screen so i can enter my user/pass then shuts off saying no video input.

any clues? i'm sure its probably something simple.

---

### Post by rsambuca on 2007-11-15
Did you make a backup of your original xorg first?

---

### Post by blinger on 2007-11-15
yes, i did make a back up, ill try that.

---

### Post by blinger on 2007-11-15
i replaced the xorg with the original, and still no go.

---

### Post by rsambuca on 2007-11-15
If the xorg worked originally, then it should work now.  However, if you are sure you did it correctly, you can start fresh with a new xorg.```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by blinger on 2007-11-15
i walked through the new xserver-xorg and it yielded the same results... could something i changed in the screen and graphics menu make this happen? i'm not positive if I made any changes there but its a possibility

---

### Post by blinger on 2007-11-16
anyone have some insight?

---

