---
title: "[SOLVED] screen resolution"
date: 2007-10-08
forum: Multimedia &amp; Video
---

### Post by jrharvey on 2007-10-08
I have been trying to figure this one out for a while. I have a nvidia 8500 GT video card and when ubuntu boots up it always starts out at 1024x768. My monitor supports 1280x1024. Every time I log in I have to change the resolution to 1280x1024 but when I restart it is back to the smaller res. I dont understand why I have to fix it everytime I restart. Is there a way to permenantly set the resolution so that I dont have to redo it every time? On the last thread I started they told me to log in as root and then set my resolution but it did not work. I eventually gave up but it just gets soooo anoying having to fix it every time.

---

### Post by jrharvey on 2007-10-08
I forgot to mention that I am in Fiesty.

---

### Post by wolfen69 on 2007-10-08
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by jrharvey on 2007-10-08
thank you it worked. Im not sure why the last guy said to log in as root. That didnt do a thing.

---

