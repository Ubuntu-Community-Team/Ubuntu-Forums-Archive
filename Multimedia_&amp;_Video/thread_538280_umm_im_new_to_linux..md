---
title: "umm im new to linux."
date: 2007-08-29
forum: Multimedia &amp; Video
---

### Post by zDOODY on 2007-08-29
how do i change the resolution from 1024X768 to 1280X1024

Im not sure how to do much so can anyone help me plz!

---

### Post by lonce on 2007-08-29
You can go to the settings menu and change it.  

If the resolution is not listed there, you will have to add it to your xorg.conf and then restart your xserver.

---

### Post by Marat Galiev on 2007-08-30
sudo nano /etc/X11/xorg.conf

find section :
```

Identifier     "Default Screen"
    Device         "Default Card"
    Monitor        "Universal Monitor"
    DefaultDepth    24

    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"

```
and edit it like this:
```

Identifier     "Default Screen"
    Device         "Default Card"
    Monitor        "Universal Monitor"
    DefaultDepth    24

    SubSection     "Display"
        Depth       24
        Modes      **"1280x1024"** "1024x768" "800x600" "640x480"

```
but in the gnome menu you can find tool for adjusting screen resolution.

---

### Post by zDOODY on 2007-08-31
Thank you very much ! It was alot of help and i learned something new :D

---

### Post by zDOODY on 2007-08-31
now i have  a new problem the desktop (at 1280x1024) will not stay still i have to move mouse to move around on it.... Anybody know the problem ? and if it helps i used this resolution when i had windows and it worked fine no scrolling desktop so im pretty sure that my hardware can handle it.

---

### Post by zDOODY on 2007-09-03
bump :(

---

