---
title: "Rhythmbox Internet radio stations missing"
date: 2010-12-14
forum: Multimedia Software
---

### Post by PJSingh5000 on 2010-12-14
The default Internet radio stations in Rhythmbox were missing.

In case anyone runs into this problem, here is a solution that worked for me...

I do not know exactly what caused the radio stations to disappear, but it might have been an improper shut-down or a crash of Rhythmbox.  I experienced this problem on Ubuntu Maverick 10.10 x64 with Rhythmbox 0.13.1.

First, I tried completely removing Rhythmbox and reinstalling it using the following commands, but this did not solve the problem.  (If you follow the three steps below, you probably don't need to reinstall Rhythmbox as I did).
```

$ sudo apt-get autoremove --purge rhythmbox
$ sudo apt-get install rhythmbox

```

I found that the rhythmdb.xml had no radio station entries in it.  To remedy this, an Internet search revealed that you must remove the existing file, and create a new 0kb file.  Finally launch Rhythmbox, and it will automatically populate the default radio stations into the new file.  (If you do not create a new 0kb file, Rhythmbox won't add the radio stations).

Here are the steps...
**(1)** Close Rythmbox.
**(2)** Create a new empty rhythmdb.xml file...
```

$ rm ~/.local/share/rhythmbox/rhythmdb.xml
$ touch ~/.local/share/rhythmbox/rhythmdb.xml

```
**(3)** Now start Rythmbox.

---

### Post by guenthert on 2010-12-21
Thanks for your efforts, but this doesn't seem to solve the issue in version 0.12.8 (Ubuntu 10.04).

After an hour of trying I gave up and just added my favorite i-radio station manually.

Would be nice if rhythmbox had a 'restore DB' button (or cmd-line option) as it tends to forget about my mp3s too (e.g. if the NFS server holding them isn't ready yet).

---

### Post by d029940 on 2011-02-12
Hello,

there is a separate package rhythmbox-radio-browser in Ubuntu Maverick 10.10 x64 for Rhythmbox 0.13.1.

Check if it is installed.

I did the following:
- Uninstalled all rhythmbox packages
- removed ~/.local/share/rhythmbox, ~/.cache/rhythmbox, ~/.gconf/apps/rhythmbox
- installed rhythmbox again, including rhythmbox-radio-browser package.

Now the internet radio stations are available again.

---

### Post by tsx2424 on 2012-01-13
How Can I find the radio station file?I can't listen the radio station.It said that "File not found"

---

