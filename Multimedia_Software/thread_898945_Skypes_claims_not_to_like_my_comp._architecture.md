---
title: "Skypes claims not to like my comp. architecture"
date: 2008-08-23
forum: Multimedia Software
---

### Post by spencercarran on 2008-08-23
I have a Macbook 3,1 (Intel Core 2 Duo) with Ubuntu Hardy 64-bit installed. On the Skype website, when I downloaded the .deb for the Linux version, the package installer gives "Error: Wrong architecture 'i386.'" Is there some way around this? It seems odd that a program would require a 32-bit system and not work in a 64-bit system.

---

### Post by Sam Lars on 2008-08-23
You can do
```
sudo dpkg -i --force-architecture package.deb
```
and it will install a 32-bit package.
It's a good idea to also install [getlibs]("http://ubuntuforums.org/showthread.php?t=474790") to make sure you have the right libraries for the package.

---

