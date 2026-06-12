---
title: "ati driver for x1950 or x series"
date: 2007-06-10
forum: Multimedia &amp; Video
---

### Post by approaching on 2007-06-10
I have been having some issues getting up my x1950 video card to do any sort of 3d acceleration. it is displaying in the proper resolution etc, but it's just not getting to 3d. i have gone through ati.com and installed their drivers through gui, but then it advises a reboot then to run 'aticonfig --initial' to wright to the xorg.conf file and this is what i get:

aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.

$ aticonfig --initial --input=/etc/X11/xorg.conf
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-0
aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.

im not sure if this is related to any sort of bug, let alone whether it would be attributed to kubuntu or ati. or is this that i am using kubuntu rather than ubuntu. im not sure, but when i went to their release notes on their site there is a bit of this which makes me think that is the case.

Before attempting to install the ATI Catalyst™ Linux software suite, the following software must be installed:

    * XOrg 6.7, 6.8, 6.9, 7.0, 7.1 or 7.2; XFree86 version 4.3
    * Linux kernel 2.4 or higher
    * glibc version 2.2 or 2.3
    * POSIX Shared Memory (/dev/shm) support is required for 3D applications 

im not 100 percent aware of what all that really is, but apt-get seems to think that i have it all, or with a disturbingly simular package name, and in my eyes is only attributed to a newer version etc. any ideas?

---

### Post by Ek0nomik on 2007-06-10
I have an X1400 on my laptop, and following this worked like a charm.

[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

or you can follow this:

[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

The latter has your aticonfig command, but as I was going to suggest, you should try adding "sudo" in front of it.

---

### Post by bourger on 2007-07-28
[quote=approaching]aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.[/quote]
Do the same but as a superuser, i.e.:
```
sudo aticonfig --initial
``` etc.

---

