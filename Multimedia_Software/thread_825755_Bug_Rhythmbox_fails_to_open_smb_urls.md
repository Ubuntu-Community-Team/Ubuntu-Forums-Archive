---
title: "Bug: Rhythmbox fails to open smb:// urls"
date: 2008-06-11
forum: Multimedia Software
---

### Post by jdaniel4 on 2008-06-11
Greetings,

If I use nautilus to navigate to a samba shared folder and try to open a .mp3 file with rhythmbox, rhythmbox promptly crashes with a segfault.  I can duplicate this bug from the terminal:

> rhythmbox smb://businessvostro/.../somedirectory/somefile.mp3
Segmentation fault

Interestingly, I can load a directory instead of a file just fine.   That is, this command

> rhythmbox smb://businessvostro/.../somedirectory

loads and plays all .mp3 files in somedirectory including the file somefile.mp3 listed above.

Any ideas as to what subsystem is failing, or where I should file a bug report?

I am using Ubuntu 8.04, fresh install.

Thanks,
   --Joel Daniels

P.S. Totem can play these files without any problem.

---

