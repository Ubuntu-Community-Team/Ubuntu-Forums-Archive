---
title: "No Xorg?"
date: 2010-02-09
forum: Multimedia Software
---

### Post by RedSingularity on 2010-02-09
I see that 9.10 doesn't use the xorg file anymore.  What am i going to edit now?  I just installed the ATI graphics driver and now i need to have ubuntu use it instead of the vesa driver.  How can this be done with no xorg conf file?

---

### Post by HappyFeet on 2010-02-09
I believe you will have to run
```
 gksudo fglrx-amdcccle
```
then make some kind of change, save, and then an xorg.conf file will be created.

[Here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") is some more info on ATI drivers in ubuntu.

---

### Post by Melcar on 2010-02-09
When you run "aticonfig --initial" it should create a xorg.conf file in the usual location.  If you want to generate one beforehand though, do:

```
sudo Xorg -configure
```


... after you kill X.  That drops *xorg.conf.new* into your root folder.  Just move it to /etc/X11/ and rename it.

---

### Post by RedSingularity on 2010-02-09
Ahh very good.  Thanks guys.

---

### Post by HappyFeet on 2010-02-09
> **Melcar said:**
> When you run "aticonfig --initial" it should create a xorg.conf file in the usual location.  If you want to generate one beforehand though, do:

```
sudo Xorg -configure
```


... after you kill X.  That drops *xorg.conf.new* into your root folder.  Just move it to /etc/X11/ and rename it.

Thanks for the info. I have never used ati in linux.

---

