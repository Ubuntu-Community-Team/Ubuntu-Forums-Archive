---
title: "OSX/Ubuntu dual boot - How do I boot Ubuntu automatically?"
date: 2006-10-28
forum: Mac OSX
---

### Post by eqqfooyoung on 2006-10-28
I am dualbooting OSX and Ubuntu on a Mac Book Pro.  Does anyone know of a way to automatically boot Linux as opposed to the Mac OS?  I have already tried booting into the Mac OS > apple > system preferences > startup disks but there is no option for changing it to linux or windows.  Is there some configuration file that I can edit or another way to make it boot the way I want?  I hardly ever use the Mac OS and I don't want to have to press the option key every time I boot it up.

---

### Post by Darrious on 2006-10-30
Have you looked into Gnome Partition Editor

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by Alfa989 on 2006-10-31
> **eqqfooyoung said:**
> I am dualbooting OSX and Ubuntu on a Mac Book Pro.  Does anyone know of a way to automatically boot Linux as opposed to the Mac OS?  I have already tried booting into the Mac OS > apple > system preferences > startup disks but there is no option for changing it to linux or windows.  Is there some configuration file that I can edit or another way to make it boot the way I want?  I hardly ever use the Mac OS and I don't want to have to press the option key every time I boot it up.

If you don't use Mac OS X why did you get a Mac anyway?:-k

---

### Post by eqqfooyoung on 2006-11-01
> **Darrious said:**
> Have you looked into Gnome Partition Editor

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

I am not 100% sure, but I do not believe a partition editor will help.  I have to use bootcamp because it needs to do something with the bios to allow it to boot Ubuntu.  I don't think this is a partition issue but more of a bootcamp setting or hack.

Please let me know if you disagree or can explain more on your partition idea.

---

### Post by doobit on 2006-11-25
> **Alfa989 said:**
> If you don't use Mac OS X why did you get a Mac anyway?:-k

There's no other notebook PC with such a nice looking enclosure.
If PC makers would put more effort into case design, and install Linux instead of Windows, then I doubt people would be buying so many Macs.

:-k

---

### Post by AlphaMack on 2006-11-26
Start from here.  Boot into Ubuntu and in the Terminal type

```
sudo ybin -v
```

This should bring yaboot back and automatically load the kernel if it is left idle at the selection prompt.

---

### Post by Ptero-4 on 2006-12-01
> **alphasubzero949 said:**
> Start from here.  Boot into Ubuntu and in the Terminal type

```
sudo ybin -v
```

This should bring yaboot back and automatically load the kernel if it is left idle at the selection prompt.

AlphaSubZero. The OP is using an Intel-based Mac, hence yaboot (a ppc bootloader) won't work, in fact he doesn't have it at all since it's for Linux PPC, not linux x86 which intel macs use. What he needs is rEFIt or elilo to boot his ubuntu.

---

### Post by AlphaMack on 2006-12-04
I stand corrected.

---

