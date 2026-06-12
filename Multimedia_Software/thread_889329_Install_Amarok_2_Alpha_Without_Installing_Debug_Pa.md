---
title: "Install Amarok 2 Alpha Without Installing Debug Packages"
date: 2008-08-14
forum: Multimedia Software
---

### Post by eightmillion on 2008-08-14
Those of you who have tried to install the amarok-kde4 package from the repositories may have noticed that it has among its dependencies a couple of huge -dbg packages totalling over 600 MB unpacked. This was done at the request of the upstream amarok developers. Amarok 2 alpha doesn't depend on these packages in the normal sense of the term. This is from the package description:
> 
NOTE: this is an alpha quality release, and therefore a lot of crashes
and bugs are to be expected, the Amarok team as well as the Ubuntu team kindly
asks you to report all issue at [http://bugs.kde.org](http://bugs.kde.org)

The debug package will make bug reports more useful.

If you would like to try out amarok-kde4 and don't have or don't want to devote 600 MB to do it, I've packaged my own version for that purpose. It's available for [**download here.**]("http://www.filedropper.com/amarok-kde4186-0ubuntu1hardy0ppa2i386")

This package does not differ from the official repository version other than the removal of the dependency on the debug packages. I will try to keep this post updated as newer versions become available.

---

### Post by jpeddicord on 2008-08-14
Moved out of Tutorials & Tips because it is a single deb package and not really a tutorial. Also, the debug symbols are probably installed with good reason: it will crash, and you can't submit a report without them. ;)

---

### Post by eightmillion on 2008-08-15
> Moved out of Tutorials & Tips because it is a single deb package and not really a tutorial. Also, the debug symbols are probably installed with good reason: it will crash, and you can't submit a report without them.
Thanks, I wasn't sure where to put it. You can submit bug reports without having the debug symbols installed, they just might not be at all useful to the developers. I suppose I should make it clear that if you are planning on running amarok-kde4 and plan on submitting bug reports, this is not for you.

---

