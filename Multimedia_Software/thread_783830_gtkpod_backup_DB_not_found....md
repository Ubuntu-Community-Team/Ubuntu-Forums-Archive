---
title: "gtkpod backup DB not found...?"
date: 2008-05-06
forum: Multimedia Software
---

### Post by euxneks on 2008-05-06
I have a strange error:

```
Error opening '/home/john/.gtkpod/backupDB_2' for writing (No such file or directory).

Error opening '/home/john/.gtkpod/backupDB_2.ext' for writing (No such file or directory).


```

As far as I can tell, this was a backupDB I used at work to upload music to my computer

I've tried to set this to something else, but it's not changing.  Can anyone suggest a site I could peruse or even a solution? Or, where the preferences are that contain the backupDB information?

I'm using Hardy and gtkpod-aac (gtkpod 0.99.12)

Thanks,

---

### Post by Kat Crichton-Seager on 2010-08-07
I had this problem, when I moved my home folder to another distro.  Deleting the ~/.gtkpod folder solved it.  Be warned that it will delete the metadata for your library, so you will have to add folders/files again.

I expect there is a less extreme way of solving this issue though! ;)

---

