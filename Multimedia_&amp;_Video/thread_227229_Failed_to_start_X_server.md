---
title: "Failed to start X server"
date: 2006-08-01
forum: Multimedia &amp; Video
---

### Post by jpknhtp on 2006-08-01
.

---

### Post by denisvj on 2006-08-01
edit xorg.conf  and change in the Section "Device"  the option
Driver with "vesa" , maybe this help.

/etc/X11/xorg.conf .

Hope this help.

---

### Post by tseliot on 2006-08-01
boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

Type:
```
reboot
```

The Xserver should work fine

---

### Post by jpknhtp on 2006-08-01
.

---

