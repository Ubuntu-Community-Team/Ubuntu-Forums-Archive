---
title: "Xubuntu Karmic - sound accessible from command line login, but not X windows???"
date: 2009-11-05
forum: Multimedia Software
---

### Post by lloyd_b on 2009-11-05
Just upgraded to Karmic, and I've encountered a problem that makes no sense.

I do not run GDM - my system boots to a command line login, and I manually run "startx" to bring up X Windows (yeah - I'm a Linux old-timer :))

At the command line, the sound system works fine.  I can use alsamixer to set volumes, and play music via mpg123.

Once I start X Windows, this changes.  In X, if I open up a terminal window, and run "aplay -l" (to list devices), I get:```
lloyd@dell:~$ aplay -l
aplay: device_list:223: no soundcards found...
```

No sound programs (I run Audacious2 for the most part, but I get the same results from Exaile) can access the sound.

Now for the really weird part - If I run "sudo audacious2", then sound *does* work.

Summary - From a command-line login, my regular user can access the sound devices.  From X, my regular user cannot, but root can.

Color me confused...

Lloyd B.

---

### Post by lloyd_b on 2009-11-06
Okay, found the solution.  I had done a clean install, but used the "/home" from the previous install.

I went through the files in ".config", and killed all of those that related to sound.

After that, everything is working, so it was just some sort of conflict between the XFCE settings from the previous version and the current version.

Lloyd B.

---

