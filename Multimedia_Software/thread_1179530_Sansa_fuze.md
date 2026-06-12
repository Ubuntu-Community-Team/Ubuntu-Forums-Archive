---
title: "Sansa fuze"
date: 2009-06-05
forum: Multimedia Software
---

### Post by Jazleah on 2009-06-05
I receive error when I plug in my SANSA FUZE 
Cannot mount Volume
Invalid mount option when attempting to mount the volume.

that is the only thing it states. Any ideas?  :-k
thanks

---

### Post by e.m.fields on 2009-11-22
Hey Jaz.  I haven't been able to get mine to detect at all, at this point an error message would be almost a relief.  =)

Have you found a solution yet?
Please someone respond if you've figured out how to get Sansa Fuze detected and working in ubuntu 9.04 and I'll add it to a "solved" thread

---

### Post by N00b-un-2 on 2010-01-02
set your Fuze to MSC mode.  Plug it in.  open Gparted and figure out which device is your Fuze.  It should show up at /dev/sdb, /dev/sdb-1 or something like that.  Once you've figured out where it's at, open a terminal and enter 
```
sudo mount /dev/sdb /media/Fuze -t vfat

```
From here, your Fuze should be mounted.  Right click on the Fuze's icon and navigate to 'properties>volume>settings' and check that there is nothing written here.  Just to be safe make sure to do the same for the 'drive' tab as well.  Then unmount and unplug the Fuze.  The next time you plug it in it should work fine.  Let me know how it goes.

---

