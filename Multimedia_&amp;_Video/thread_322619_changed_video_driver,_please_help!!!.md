---
title: "changed video driver, please help!!!"
date: 2006-12-20
forum: Multimedia &amp; Video
---

### Post by hookem10 on 2006-12-20
in xorg.conf i changed my driver from i810 to 915resolution and now i can't boot into ubuntu, as there is nothing graphical to display.
anyway i can change that back? thanks.

---

### Post by acturneruk on 2006-12-21
Does it boot to the console? Can you log in? If not, boot into recovery mode (select it in the Grub menu), and then edit xorg.conf:-

```
sudo nano -w /etc/X11/xorg.conf
```

Ctrl-X, followed by Y to save and exit.  Then reboot.

HTH

---

### Post by hookem10 on 2006-12-21
thank you!! that worked perfectly.
only now, my audio doesn't work and i don't know how to fix that.
im on an inspiron e1505 and it was working until i changed that and now it doesn't.

---

