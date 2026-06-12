---
title: "vlc automatically opens when drives are mounted"
date: 2011-10-18
forum: Multimedia Software
---

### Post by Tig3rzhark on 2011-10-18
Ever since I upgraded to 11.10 on my netbook, vlc would automatically open when I mount my external hard drives.  I find that to be annoying.

Is there a way that I can fix this problem?  I would rather have the file manager window appear for mounted hard drives.

---

### Post by wolfen69 on 2011-10-18
Delete your vlc config file and restart vlc (if you don't really need it) and see what happens.

---

### Post by Tig3rzhark on 2011-10-18
> **wolfen69 said:**
> Delete your vlc config file and restart vlc (if you don't really need it) and see what happens.

How do I delete the vlc config file?  Where do I find it?

---

### Post by mc4man on 2011-10-18
Simple fix, quite common with upgrades - 
Run this in a terminal

```
gedit ~/.local/share/applications/mimeapps.list
```

In the [Default Applications] section there will be a line starting with
inode/directory=
Delete the line

---

### Post by Tig3rzhark on 2011-10-18
I deleted the config file, and restarted the Vlc program.

Result: nothing changed.  Vlc still opens automatically when drives are mounted.

---

### Post by Tig3rzhark on 2011-10-19
> **mc4man said:**
> Simple fix, quite common with upgrades - 
Run this in a terminal

```
gedit ~/.local/share/applications/mimeapps.list
```

In the [Default Applications] section there will be a line starting with
inode/directory=
Delete the line

Thank you very much.  All is right with the world.

---

### Post by Lori700698 on 2011-10-19
> **mc4man said:**
> Simple fix, quite common with upgrades - 
Run this in a terminal

```
gedit ~/.local/share/applications/mimeapps.list
```

In the [Default Applications] section there will be a line starting with
inode/directory=
Delete the line

Your my hero tonight!  
I thought it would take hours to dig this solution up, what a silly little annoyance this is!

---

