---
title: "Problem installing Flash Player"
date: 2009-09-28
forum: Multimedia Software
---

### Post by poker158149 on 2009-09-28
[I]I just installed Ubuntu 9.04 on my computer.

I'm trying to install flash player for firefox.

Everytime I download the .deb file for Ubuntu and try to run it, this comes up:

Error: Dependency is not satisfiable: libnspr4-dev

And I can't install it.

What's the problem?[/I]     

---------------------------------

NEVERMIND!

I just had to install the Ubuntu system updates.

Now it works fine.

---

### Post by lovinglinux on 2009-09-28
Install from the repositories:

```
sudo apt-get install flashplugin-nonfree
```

Also make sure you remove gnash and swfdec:

```
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
```

More info at [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567).

---

