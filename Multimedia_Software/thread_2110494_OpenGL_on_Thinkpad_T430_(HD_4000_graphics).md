---
title: "OpenGL on Thinkpad T430 (HD 4000 graphics)"
date: 2013-01-30
forum: Multimedia Software
---

### Post by montag dp on 2013-01-30
Hi,

I recently bought a Thinkpad T430 laptop with HD 4000 integrated graphics.  There seems to be something wrong with the OpenGL support.  I first noticed it when I installed cairo-dock and wasn't able to use the OpenGL version.  It will run, but the icons don't display.  Yesterday I was using a different program (called Tecplot 360 FWIW) to create some plots.  When I tried to export them to .png files, it complained about my OpenGL only supporting maximum image sizes of -1 x -1, which I guess means I can't use it to export images because of whatever this problem is with the OpenGL support.

Does anyone have an idea what could be wrong or how it could be fixed?  I'm guessing it probably has to do with some packages that I need to install, but I'm not sure which ones.  The standard mesa libraries seem to be present.

Thanks.

---

### Post by montag dp on 2013-01-31
Any ideas?  I think I'm going to try an LTS-based release (currently using Mint 14 KDE) on Live USB to see if that makes any difference.  If not, I will chalk it up to the Ivy Bridge / HD4000 graphics being new and hope it gets fixed in later updates.

Speaking of which, does anyone know how I could go about submitting a bug report for an issue like this?  All I know right now is that the OpenGL support is not working quite right, but I don't know how to find out *what* is actually the bug.

---

### Post by linrunner on 2013-01-31
EDIT: proper reading helps ...

---

### Post by Bucky Ball on 2013-01-31
*Thread moved to **Multimedia & Video***

---

### Post by montag dp on 2013-01-31
Well, I tried both Xubuntu 12.04 and Mint 13 KDE on a Live USB, and they both had the same problem.  So I guess I will just have to wait and hope it gets fixed as drivers are improved.

---

### Post by miousername on 2014-01-10
Try this:

[http://ubuntuforums.org/showthread.php?t=2198626](http://ubuntuforums.org/showthread.php?t=2198626)

---

