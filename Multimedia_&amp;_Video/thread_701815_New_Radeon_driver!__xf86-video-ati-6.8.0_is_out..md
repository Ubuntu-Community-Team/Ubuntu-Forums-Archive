---
title: "New Radeon driver!  xf86-video-ati-6.8.0 is out."
date: 2008-02-19
forum: Multimedia &amp; Video
---

### Post by JPorter on 2008-02-19
**xf86-video-ati-6.8.0** has just been released.

Full annnouncement:

[http://lists.freedesktop.org/archives/xorg/2008-February/032992.html](http://lists.freedesktop.org/archives/xorg/2008-February/032992.html)


Announcement on [Phoronix]("http://www.phoronix.com/scan.php?page=news_item&px=NjMzOQ"):
> Open-Source ATI 6.8.0 Driver Released
Posted by Michael Larabel on February 19, 2008

It's been a long time in the making, but the xf86-video-ati driver has finally reached version 6.8.0! The major improvements in this new version include the drivers now all using libpciaccess, restructuring of the ATI wrapper, Radeon support for the R500/600 series using the AtomBIOS, initial Render acceleration support for the R300/400 series, improve BIOS/driver interaction, and many other changes. 


This is the "radeon" driver in Ubuntu, for those of you who don't know.  Hopefully someone will make Ubuntu packages for this very soon, so we don't have to wait weeks or months for the repos.

---

### Post by balsamo on 2008-02-19
could somebody give some instructions on how we can set up and use the new driver without waiting for new packages ??

I mean configuring this manually. it would be great sine this driver adds support for r5xx and r6xx ...

i've tried compiling the source but it complains about libdrm 2.2 missing and i don't know how to install correctly in ubuntu.

someone can help ?

---

### Post by sloggerkhan on 2008-02-19
you probably need to install the -dev version of every package it complains about when you  go to compile it.

---

### Post by balsamo on 2008-02-19
thanks you for your response. i've installed libdrm-dev and no complains. but compile error now :


In file included from atidripriv.h:40,
                 from atistruct.h:40,
                 from atimach64io.h:37,
                 from atibus.c:32:
/usr/include/GL/glxint.h:28:19: error: GL/gl.h: No such file or directory
In file included from atidripriv.h:40,
                 from atistruct.h:40,
                 from atimach64io.h:37,
                 from atibus.c:32:
/usr/include/GL/glxint.h:95: error: expected specifier-qualifier-list before 'GLboolean'
make[2]: *** [atibus.lo] Error 1
make[2]: Leaving directory `/home/nbourdeau/downloads/ati/xf86-video-ati/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/nbourdeau/downloads/ati/xf86-video-ati'
make: *** [all] Error 2

don't know what to do with that ...

---

### Post by JPorter on 2008-02-20
Pferraro with the assist!  Debian packages are out.

> **pferraro said:**
> For the impatient folks:
[http://packages.debian.org/sid/xserver-xorg-video-ati](http://packages.debian.org/sid/xserver-xorg-video-ati)

---

