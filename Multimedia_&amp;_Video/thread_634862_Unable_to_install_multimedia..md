---
title: "Unable to install multimedia."
date: 2007-12-08
forum: Multimedia &amp; Video
---

### Post by TemanX on 2007-12-08
Error while installing .......:(

temanx@temanx-desktop:~$ sudo apt-get install libdvdcss2 w32codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate

---

### Post by acoustibop on 2007-12-08
You need the Medibuntu repository included in your lists for libdvdcss2, TemanX.  See the [Ubuntu Medibuntu page]("https://help.ubuntu.com/community/Medibuntu").  I think there is also a css version in the Ubuntu repositories, although most people seem to prefer the Medibuntu version - but if you've already installed this, you may not be able to install the Medibuntu one unless you remove it.  AIR I had that issue at one time.

The other particularly useful package from Medibuntu for playing many different formats is the w32codecs one.

---

