---
title: "Acer 1524 resolution 1280x800"
date: 2006-12-15
forum: Multimedia &amp; Video
---

### Post by LordOfRings on 2006-12-15
hi guys..


I cant change the resolution to 1280x800 in my laptop.

It is possible.

I dont know anything about ubuntu and it is dificult for me. .

Thanks..

---

### Post by antar on 2006-12-15
What graphics card are you using?

If it's an Intel 915, go to Synaptic and install the 915resolution package.

---

### Post by LordOfRings on 2006-12-15
> **antar said:**
> What graphics card are you using?

If it's an Intel 915, go to Synaptic and install the 915resolution package.

i found for intel but not for nvidia .. 

nvidia go 5700 ..

---

### Post by LordOfRings on 2006-12-15
> **LordOfRings said:**
> i found for intel but not for nvidia .. 

nvidia go 5700 ..

any idea ? .

---

### Post by quinnman on 2006-12-15
You can do this manually by editing /etc/X11/xorg.conf and adding the desired resolution "1280x800". Alternatively, install the latest stable nvidia drivers (following this thread [http://www.ubuntuforums.org/showthread.php?t=255929](http://www.ubuntuforums.org/showthread.php?t=255929)) and set the resolution in GUI using the nvidia tool.

---

### Post by LordOfRings on 2006-12-15
> **quinnman said:**
> You can do this manually by editing /etc/X11/xorg.conf and adding the desired resolution "1280x800". Alternatively, install the latest stable nvidia drivers (following this thread [http://www.ubuntuforums.org/showthread.php?t=255929](http://www.ubuntuforums.org/showthread.php?t=255929)) and set the resolution in GUI using the nvidia tool.

ok solved.. thanks..

it was simlple I just changed the xorg.conf .

---

