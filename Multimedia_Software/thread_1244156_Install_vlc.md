---
title: "Install vlc"
date: 2009-08-19
forum: Multimedia Software
---

### Post by kdroxx on 2009-08-19
Hello, I just installed Ubuntu 9.04 and am not familiar with the installation process.
Please explain how to install.
Also, where can I find the installation package of vlc?

---

### Post by binbash on 2009-08-19
[http://www.ubuntu-inside.me/2009/04/howto-fix-integrated-video-bug-at-vlc.html](http://www.ubuntu-inside.me/2009/04/howto-fix-integrated-video-bug-at-vlc.html)

Read update part for the new repository.

---

### Post by Zack McCool on 2009-08-19
Open the terminal and type:
```

sudo apt-get install vlc

```
Enter your user password (it will not echo), hit enter, and answer Y if you are asked if you're sure.

This will pull vlc and all of it's dependencies from the multiverse repository.

---

### Post by wotsit on 2009-08-19
go to system> administration> synaptic package manager
 
search for vlc
 
and mark and click apply
 
make sure you have the universe repositories enabled

---

### Post by kdroxx on 2009-08-21
Thanks for the help guys, I managed to install VLC.
But I need to install it on other computers as well.
Where can I find the .deb or compile .deb from .tar.bz2 ?

---

### Post by Zack McCool on 2009-08-22
The problem is that it isn't just one deb.  It has several dependencies, and you'd need all of them to be available to get it installed right.

The easiest way is to have each of those machines connected to the net, with the proper repo's enabled, and do a sudo apt-get install vlc.

Failing that, you'll want to do the following on your PC:

sudo apt-cache showpkg vlc

And make sure that you have the debs from each of those dependencies...

---

