---
title: "Install Libcss2 without internet connection?"
date: 2008-10-01
forum: Multimedia Software
---

### Post by Darkchef on 2008-10-01
Hey,

I want to add encrypted DVD support for my desktop, although I do not have an internet connection there. is there a deb package available for download that will configure this without an internet connection. 

Any help would be appreciated, thanks

---

### Post by Yellow Pasque on 2008-10-01
[http://packages.medibuntu.org/](http://packages.medibuntu.org/) Pick your distro and get libdvdcss2. Just make sure you have the dependencies (In this case, it's only libc6, which you should have).

---

### Post by wolfen69 on 2008-10-01
[Here]("http://downloads.videolan.org/pub/videolan/libdvdcss/1.2.9/deb/") you go.

---

### Post by Yellow Pasque on 2008-10-01
> **wolfen69 said:**
> [Here]("http://downloads.videolan.org/pub/videolan/libdvdcss/1.2.9/deb/") you go.
Note that this link doesn't have the latest version (and only has i386 versions).

---

### Post by mc4man on 2008-10-01
Just for info's sake the latest version is 1.2.10-0  (aug. -sept 2008)
Available from videolan, medibuntu (intrepid), and debian-multimedia

The only diff. between the 3 is the min. version of libc6 

Videolan - 2.3.6-6 (dapper? and up
Medibuntu -  2.4    (edgy and up
Debian - 2.7-1      (hardy and up

---

### Post by Darkchef on 2008-10-04
Cheers all, ive downloaded the deb file and installed the codec with no problems at all.

---

