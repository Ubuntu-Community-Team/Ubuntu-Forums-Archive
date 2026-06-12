---
title: "I lost my frontend menus - How do I get them back?"
date: 2009-10-12
forum: Mythbuntu
---

### Post by cat2005 on 2009-10-12
**I lost my frontend menus - How do I get them back?**

This is what happened:

- Went to "Applications" - "Sound and Video" - "Mythtv Frontend"
- Found several choices (Watch TV, Appearance, etc. . .)
- Selected "Appearance" and changed something, then I got a screen stating "pre-scaling image" screen that hung for a long time but finally finished, then I automatically exited mythfrontend.
- Again, I went to "Applications" - "Sound and Video" - "Mythtv Frontend" but when I clicked "Mythtv Frontend" I just received a very, very short "Select Your Language" and "No UPnP found"
- Then I am taken to "Database Configuration" but everything I do yields the same message:  "Can not login database?"  Selecting "OK" is the only given step.

**I lost my frontend menus - How do I get them back?**

/ running Mythbuntu 9.04
// I forgot to add:  I have the same problem with my backend menus.  They are also gone and replaced by the same screens which replaced the frontend menus.

---

### Post by uncle hammy on 2009-10-12
Sounds like your backend has stopped 
```
pgrep mythbackend
```
any pid returned?

---

### Post by cat2005 on 2009-10-13
> **uncle hammy said:**
> Sounds like your backend has stopped 
```
pgrep mythbackend
```
any pid returned?
 
 
uncle hammy,
 
I tried that, but nothing happened. No PID or anything was returned.
 
I will just do a fresh install.
 
Thanks for your time.

---

