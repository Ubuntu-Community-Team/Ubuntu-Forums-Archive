---
title: "Migrating to Ubuntu Studio"
date: 2008-11-29
forum: Multimedia Software
---

### Post by ontik on 2008-11-29
Is it possible to change of from the standard desktop Ubuntu 8.10 to Ubuntu Studio 8.10 without doing a complete re-install?  And of course not just installing all the apps bundled with studio.


ontiK.

---

### Post by jpeddicord on 2008-11-29
Install the [ubuntustudio-desktop]("apt:ubuntustudio-desktop") package, which will pull in the complete Ubuntu Studio system. :)

---

### Post by ontik on 2008-11-29
Excellent.  Will do. 

Is it the full Ubuntu Studio experiene of the just the catalogue of apps?


ontiK.

---

### Post by jpeddicord on 2008-11-29
> **ontik said:**
> Excellent.  Will do. 

Is it the full Ubuntu Studio experiene of the just the catalogue of apps?


ontiK.

It's the full experience, though because you're installing from base Ubuntu your desktop theme will not be automatically applied. Just pick the studio theme from System > Preferences > Appearance and you're all set.

---

### Post by ontik on 2008-11-29
Cool, should be fun.  (Once I sort out this bloody graphic issue I've just acquired upgrading from Hardy grrrrrrr!)


ontiK.

---

### Post by markbuntu on 2008-11-29
If you are using the nvidia drivers, the rt kernel will not load the nvidia kernel modules and you will get an x failure on reboot. You should remove this driver before installing the rt kernel. This may also happen with the ati fglrx driver but I have not tried it yet.

---

