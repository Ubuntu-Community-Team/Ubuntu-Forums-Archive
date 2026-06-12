---
title: "Zune hard drive under ubuntu"
date: 2008-10-21
forum: Multimedia Software
---

### Post by magikid on 2008-10-21
I've been searching and I can't seem to find if it is possible to mount the Zune as a hard drive in Ubuntu.  I'm not looking to transfer music or sync it.  I just want to use my Zune as an external hard drive without installing VMWare or VirtualBox.

Thanks.

---

### Post by davidcrew on 2008-10-21
I read somewhere that it is possible to run the application software for the zune through Wine...Not sure if that would mount the drive, however. 

What happens when you plug in the zune? It simply doesn't show up?

---

### Post by magikid on 2008-10-22
I heard that you could do that but I'd just as soon dual-boot since I heard that Zune under wine is such a headache.

You are correct about what happens, when I plug it in, it just doesn't show up.  I tried doing ```
sudo mount -a
```then ```
sudo mount -a -t ntfs
``` and also got nothing.

---

