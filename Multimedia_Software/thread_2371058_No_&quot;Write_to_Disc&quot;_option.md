---
title: "No &quot;Write to Disc&quot; option"
date: 2017-09-10
forum: Multimedia Software
---

### Post by charles-laferriere on 2017-09-10
Hello folks,
I'm trying to burn an iso to a dvd as a bootable disk. 
In theory, there should be the option to Write to disc (right click button). 
I tried Brasero, Iso maker and well it boils down to this:
Ubuntu does not recognize the blank disk (or perhaps drive?).
I tried more than one disk. 

Does linux have... "drivers"? 
Danke!

---

### Post by mc4man on 2017-09-10
What version of Ubuntu are you using & what file manager.
Here in 16.04/nautilus the "Write to Disc" option shows up from context menu on any valid .iso, whether there is any media in dvd drive is irrelevant.

---

### Post by charles-laferriere on 2017-09-10
I'm using 16.04 Desktop.
And File Manager.. "Files" ?
I've tried pointing to different iso files, ones that are confirmed to be good (ubuntu). 
It doesn't show up. 

uname -a
Linux BinarySupportTeam 4.10.0-33-generic #37~16.04.1-Ubuntu SMP Fri Aug 11 14:07:24 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by Autodave on 2017-09-10
I have had weird problems before with Brasero. You may want to install   xfburn  and try that. It is in the software center or synaptic.

---

### Post by mc4man on 2017-09-10
Try this, 
Make sure brasero is installed
in terminal
```
nautilus -q
```
Then restart nautilus (click on launcher icon or any folder on Desktop

Or just do a log out/in

---

### Post by charles-laferriere on 2017-09-10
Oh.

Oh :\

/runs away and hide.

The drive is not a dvd-WRITER. :\ 
:oops:

---

