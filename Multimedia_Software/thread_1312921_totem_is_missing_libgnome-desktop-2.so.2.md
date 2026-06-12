---
title: "totem is missing libgnome-desktop-2.so.2 ??"
date: 2009-11-03
forum: Multimedia Software
---

### Post by sharp11 on 2009-11-03
One day I woke up and totem stopped working. It gives this error:

```
error while loading shared libraries: libgnome-desktop-2.so.2: cannot open shared object file: No such file or directory
```

I've tried reinstalling totem. Also tried reinstalling libgnome-desktop-2 - but it is up to date and I'm afraid to remove it/reinstall bc so many things depend on it. 

This problem started before I upgraded to 9.10. I hoped the upgrade would fix it, but it hasn't.

I even tried creating a symlink libgnome-desktop-2.so.2 => libgnome-desktop-2.so.11.4.2 (which does exist on my system), but then totem dies with a different error.

---

### Post by mc4man on 2009-11-03
If you were in a position to do a fresh install at some point this issue would not exist.

I can't figure out how (or if even possible) to remove erroneous ldd's, but maybe try this

Open up synaptic, search totem and mark totem and totem-common for **complete removal** and apply. ( **Also** check the totem-gstreamer package, even if not installed, r. click on and see if a complete r. is available, if so mark .

Then double ck. in home folder -> .local/share/applications for a totem.desktop. If one is there, then delete.

**Reboot** and then install totem and see.
```
sudo apt-get install totem
```

---

### Post by sharp11 on 2009-11-03
Thanks for the suggestions. It helped me figure out what was going on ... I actually had compiled my own version of totem (a long time ago!) and had left it lying around. It was confusing things ...

Anyway, thanks a lot!

---

