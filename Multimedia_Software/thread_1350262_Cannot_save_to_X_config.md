---
title: "Cannot save to X config"
date: 2009-12-09
forum: Multimedia Software
---

### Post by Blackbooks on 2009-12-09
Hey guys,
I just got a new machine and I'm getting this error trying to save my display settings..
Any help with this?

Much appreciated!

[[IMG]http://img268.imageshack.us/img268/2127/screenshotqce.png]("http://img268.imageshack.us/i/screenshotqce.png/")

---

### Post by Blackbooks on 2009-12-09
I also ran it as sudo in a terminal and got the same error, this was the terminal output;

"VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
Undefined Device "(null)" referenced by Screen "Default Screen".

Segmentation fault"

---

### Post by darkksyde. on 2009-12-09
Its a karmic bug. I solved like this.

```
sudo rm /etc/X11/xorg.conf
```Then,

```
sudo nvidia-settings
```Then save the file as,

/etc/X11/xorg.conf

Then reboot!

---

### Post by Blackbooks on 2009-12-09
Sweet as! All looking well, thanks for the help!

---

### Post by darkksyde. on 2009-12-09
;)

---

