---
title: "Apple 30&quot; Cinema Display in 6.10"
date: 2006-12-23
forum: Multimedia &amp; Video
---

### Post by capnqwest on 2006-12-23
I'm a Gentoo refugee wanting to see what the Ubuntu fuss is all about.  Unfortunately, I only have two 30" Apple Cinema displays and can't get any better than 1024x768 on one.  I've hacked xorg.conf relentlessly all day to no avail and strangely, had no luck googling.

System specs:
Intel Core 2 Duo E6800 @2.93GHz
4 GB DDR2 RAM
4x150 10k RPM WD Raptors (will use LVM)
Nvidia 7950 GT-OC Card (512 MB RAM)

I had zero trouble out of the box on Sabayon, Mandriva 2007 and Fedora Core 6.

Has anyone been able to get the native 2560x1600 on an Apple 30" Cinema Display and if so, can you post your xorg.conf here?   I assume it's a Driver/Xorg issue but I do have the "nv" module loaded.  Not looking for any AIGLX/XGL, just a working display.

Thanks!

---

### Post by PilotJLR on 2006-12-23
You need the nVidia driver, not "nv"... the "nvidia" one will work.

You'll need to enable multiverse repos and install from there...

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by capnqwest on 2006-12-29
Cool that worked.  My problem was trying to do this with a live CD.  Once I took the plunge and installed it, this worked perfectly.

---

### Post by majoridiot on 2006-12-29
> **capnqwest said:**
> Unfortunately, I only have two 30" Apple Cinema displays... 

oh you poor unforunate soul, you... :P

---

