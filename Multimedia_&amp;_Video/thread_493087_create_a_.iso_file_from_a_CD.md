---
title: "create a .iso file from a CD"
date: 2007-07-05
forum: Multimedia &amp; Video
---

### Post by ubuntu_jazzbach on 2007-07-05
HI !!!

Does anyone know how to create a .iso file from a CD. Something like the program in Windows "Alcohol 120%" does, but in Ubuntu ??

---

### Post by stchman on 2007-07-05
> **ubuntu_jazzbach said:**
> HI !!!

Does anyone know how to create a .iso file from a CD. Something like the program in Windows "Alcohol 120%" does, but in Ubuntu ??

You can use K3B and instead of selecting an optical drive select image.  This will create a .iso file.

---

### Post by az on 2007-07-05
In gnome, you can right-click on the disk and select COPY.  Then just copy it to file.  Name it something.iso.

Alternatively, you can open a terminal and run

dd if=/dev/cdrom0 of=file.iso

---

