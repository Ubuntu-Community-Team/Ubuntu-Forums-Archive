---
title: "Blank Sceen after Boot Screen"
date: 2006-07-11
forum: Multimedia &amp; Video
---

### Post by Tristan9669 on 2006-07-11
I used the intructions at [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide) and I used method 2 and when I rebooted my computer and after the boot screen finish loading I can't see anything. Do I need to restore my xorg backup?, if so how can I?

---

### Post by tseliot on 2006-07-11
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

### Post by Tristan9669 on 2006-07-11
The grub menu timeout is set to 0, so the menu doesn't really show up. Is there a way I can launch it manually?

---

