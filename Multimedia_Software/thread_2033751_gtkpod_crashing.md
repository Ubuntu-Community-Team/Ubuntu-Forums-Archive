---
title: "gtkpod crashing"
date: 2012-07-26
forum: Multimedia Software
---

### Post by thomsmells on 2012-07-26
I'm having issues with gtkpod on lubuntu 12.04.

It just crashes all the time, whenever it tries to do almost anything.

I've been able to sync my ipod with banshee, but it just drains the CPU, and isn't very practical.

Any known reasons why gtkpod would crash whenever it tries to do anything? If not, know any other good lightweight, simple ipod manager alternatives?

Cheers.

---

### Post by ron999 on 2012-07-26
> **thomsmells said:**
> I'm having issues with gtkpod on lubuntu 12.04.

It just crashes all the time, whenever it tries to do almost anything.

Any known reasons why gtkpod would crash whenever it tries to do anything?
Hi
**gtkpod** in 12.04 repository is broken.
It will crash when you try to edit preferences.
I've compiled gtkpod from git. It works OK.
Information is here ---> [http://ubuntuforums.org/showthread.php?t=2028977]("http://ubuntuforums.org/showthread.php?t=2028977")

---

### Post by thomsmells on 2012-07-29
You're beautiful, thank you.

---

### Post by Tido on 2013-01-06
> 
**gtkpod** in 12.04 repository is broken.
It will crash when you try to edit preferences.
I've compiled gtkpod from git. It works OK. Information is here ---> [http://ubuntuforums.org/showthread.php?t=2028977]("http://ubuntuforums.org/showthread.php?t=2028977")

With this approach you **loose security** updates!
You break the chain to the ubuntu repositories.
I will now file my problem here [http://bugs.launchpad.net]("https://bugs.launchpad.net/ubuntu/+source/gtkpod/+bug/1021501"), I rather have a fixed package for the next 3 years or longer.
 
I hope others will follow me !

cheers

---

### Post by smorgado on 2013-02-26
I compiled and installed gtkpod from git but I think some libraries
get missplaced, when I run /usr/local/bin/gtkpod does not find
libgtkpod.so.1

---

### Post by Magnes Fox on 2013-06-10
To ron999, **thank you**!

> **smorgado said:**
> I compiled and installed gtkpod from git but I think some libraries
get missplaced, when I run /usr/local/bin/gtkpod does not find
libgtkpod.so.1

You need to do
```
sudo ldconfig
```
This probably happened on your next reboot, so I'm just putting this here for any future visitors to this thread.

To Tido, the instructions are how to build your own Debian package, so a newer version number should still trigger an upgrade over the version built by hand from git.  No loss of security patches.

---

### Post by Tido on 2013-06-23
> **Magnes Fox said:**
> To ron999, **thank you**!
To Tido, the instructions are how to build your own Debian package, so a newer version number should still trigger an upgrade over the version built by hand from git.  No loss of security patches.

@ Magnes Fox: This may be, but still it would be great if **you** and **everybody** who has this problem does file it on the bugtracker - may be then they solve it for all of us :D

---

