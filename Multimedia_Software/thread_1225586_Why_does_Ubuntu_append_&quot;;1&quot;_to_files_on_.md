---
title: "Why does Ubuntu append &quot;;1&quot; to files on a CD?"
date: 2009-07-28
forum: Multimedia Software
---

### Post by rexregum on 2009-07-28
I'm trying to install some old games of mine: Warcraft I and Starcraft.

Unfortunately, whenever I try to mount the CD, all of the files have ";1" appended to the file type.  And some of the ".EXE"s have been changed to ".EXA"s.

(For example, the mounted CD contains "INSTALL.EXE;1" instead of "INSTALL.EXE", and won't run through Wine.)

This is not the first time this has happened.  And it isn't just for games.

Could someone please explain why Ubuntu does this, and how to fix it?

Thank you,

rexregum

---

### Post by igorzwx on 2009-07-28
Do you really mount ISO or you doing something else?

I remember I had something like this (long ago)
when I tried to open ISO with archive manager

---

### Post by rexregum on 2009-07-28
> **igorzwx said:**
> Do you really mount ISO or you doing something else?

I right-click on the ISO file and choose "Open with Archive Mounter".  An icon of a CD-ROM drive appears on the Desktop.  I can right-click on this icon and choose "Unmount volume".

> I remember I had something like this (long ago)
when I tried to open ISO with archive manager

I've tried "Open with Archive Manager" as well.  Same result.

---

### Post by igorzwx on 2009-07-28
You should not open ISO with Archive manager.
You should mount them.

try gmountiso

howto is here:
[http://hacktivision.com/index.php/2008/02/24/how-to-mount-iso-images-in-ubuntu-the-ea?blog=2](http://hacktivision.com/index.php/2008/02/24/how-to-mount-iso-images-in-ubuntu-the-ea?blog=2)
**[How to mount ISO images in Ubuntu the easy way]("http://hacktivision.com/index.php/2008/02/24/how-to-mount-iso-images-in-ubuntu-the-ea?blog=2")**

---

### Post by rexregum on 2009-07-28
> **igorzwx said:**
> You should not open ISO with Archive manager.
You should mount them.

try gmountiso

howto is here:
[http://hacktivision.com/index.php/2008/02/24/how-to-mount-iso-images-in-ubuntu-the-ea?blog=2](http://hacktivision.com/index.php/2008/02/24/how-to-mount-iso-images-in-ubuntu-the-ea?blog=2)
**[How to mount ISO images in Ubuntu the easy way]("http://hacktivision.com/index.php/2008/02/24/how-to-mount-iso-images-in-ubuntu-the-ea?blog=2")**

Thanks, that worked! :P

---

### Post by igorzwx on 2009-07-28
Next time try this:
type in google: "ubuntu howto mount iso"
:P

---

### Post by zero777zero on 2009-07-28
i also had this problem. when using linux, do the opposite of what your intuition tells you

---

### Post by igorzwx on 2009-07-28
it is already solved, or not?

---

### Post by igorzwx on 2009-07-28
OK. Windows can spoil intuition. It is true.

---

### Post by lisati on 2009-07-28
> **rexregum said:**
> I'm trying to install some old games of mine: Warcraft I and Starcraft.

Unfortunately, whenever I try to mount the CD, all of the files have ";1" appended to the file type.  And some of the ".EXE"s have been changed to ".EXA"s.

(For example, the mounted CD contains "INSTALL.EXE;1" instead of "INSTALL.EXE", and won't run through Wine.)

This is not the first time this has happened.  And it isn't just for games.

Could someone please explain why Ubuntu does this, and how to fix it?

Thank you,

rexregum

I've noticed similar (but not identical) effects in the past: the only pattern I've noticed is when the OS reports a similarly named file in the same place that it wants to put its working copy.

---

