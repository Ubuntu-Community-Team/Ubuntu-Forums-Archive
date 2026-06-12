---
title: "Similar soft to Daemon Tools..."
date: 2009-03-17
forum: Multimedia Software
---

### Post by daGrevis on 2009-03-17
Is there any similar soft to Daemon Tools, just for Linux Ubuntu? Soft, where U can emulate CD/DVF from .ISO file... :KS

---

### Post by aninaiian on 2009-03-17
There's gmountiso in the repos if you want a gui or you could do it from nautilus with one of the scripts found at [gnome-look]("http://gnome-look.org/content/show.php/Nautilus+Scripts+Pack?content=90330&PHPSESSID=9813ff348d5075815acbcde414c8c665").  I've never actually used any of these before.  Usually, I do it via the mount command ala
```
mount -o loop /place/where/iso/is /place/i/want/to/mount/it
```
I think the nautilus script and the program are frontends to this command.

---

