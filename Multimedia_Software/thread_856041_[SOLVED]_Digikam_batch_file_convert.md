---
title: "[SOLVED] Digikam batch file convert"
date: 2008-07-11
forum: Multimedia Software
---

### Post by niceguy123 on 2008-07-11
I've installed digikam with the kipi plugin package. When I try to batch convert jpg files to png I get the following:

```
Cannot start 'convert' program from 'ImageMagick' package;
please check your installation.
``` 

Anyideas?

---

### Post by .nedberg on 2008-07-11
It looks like you don't have imagemagic installed.

```
sudo apt-get install imagemagick
```

---

### Post by AmanicA on 2008-09-10
As far as I can tell, that package is not availible on ubuntu 64bit :(
I might have to use picasa...


# sudo apt-get install imagemagick
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package imagemagick is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package imagemagick has no installation candidate

--
:guitar:

---

