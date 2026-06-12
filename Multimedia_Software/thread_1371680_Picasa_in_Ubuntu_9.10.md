---
title: "Picasa in Ubuntu 9.10"
date: 2010-01-03
forum: Multimedia Software
---

### Post by goslings on 2010-01-03
I rather like Picasa (maybe i'm alone on this)
Now i've upgraded to 9.10 it appears to be broken ?
application - Graphics - Picasa yields nothing 
picasa in a terminal yields 
```

ian@goslinux:~$ picasa
/usr/bin/picasa: line 139:  4631 Segmentation fault      "$PIC_BINDIR"/wrapper check_dir.exe.so
/usr/bin/picasa: line 175:  4727 Segmentation fault      "$PIC_BINDIR/wrapper" regedit /E $registry_export HKEY_USERS\\S-1-5-4\\Software\\Google\\Picasa\\Picasa2\\Preferences\\

```

Is it bust in 9.10 and is there a way to fix it

---

### Post by shadfc on 2010-01-04
same problem here.  any fix?

---

### Post by kellemes on 2010-01-04
Have you tried a reinstall of Picasa? This is Picasa 3.0.0 right?
It's working fine in my case.. well.. working from Arch Linux but that shouldn't make a difference I guess.

---

### Post by garryknight on 2010-01-04
It's working OK here. Picasa 3.0.0 (Build 57.4402, 0).

---

### Post by boscopup on 2010-01-21
I had this problem, but then I realized I had installed Picasa 2.7 (stable release) instead of Picasa 3.x (testing release). Picasa 3 works great. So make sure you have the right version installed. I had to add the "testing repository".

---

### Post by fscodelaro on 2010-05-27
Exactly, I had the same problem in Lucid and it is solved by adding the Google testing repository and installing Picasa 3.0.

The repo to add is 

```
deb http://dl.google.com/linux/deb/ testing non-free
``` 

The full instructions are in the following link: 

[http://www.google.com/linuxrepositories/testrepo.html]("http://www.google.com/linuxrepositories/testrepo.html")

---

