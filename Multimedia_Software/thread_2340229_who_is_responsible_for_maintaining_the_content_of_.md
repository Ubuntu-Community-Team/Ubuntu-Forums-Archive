---
title: "who is responsible for maintaining the content of this file"
date: 2016-10-16
forum: Multimedia Software
---

### Post by joverstreet1 on 2016-10-16
Who do I contact about maintaining the contents of this application ?

GNUstep application for digital still cameras - i.e. CAMERA.APP - note NOT CAMERA-APP

Thanks.

---

### Post by oldos2er on 2016-10-16
```
apt show camera.app
``` shows "Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>" so you could email that listserver address. See [https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-discuss](https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-discuss)

---

### Post by mc4man on 2016-10-17
[The source]("http://gna.org/projects/gsimageapps") hasn't been touched in 11 years so at this point nobody. Every once & a very rare while someone will push a rebuild for  various reasons.

Cut from changelog. - 
> camera.app (0.8.0-9.1build1) wily; urgency=medium

  * No-change rebuild against libgphoto2-port12.

 -- Martin Pitt <martin.pitt@ubuntu.com>  Tue, 26 May 2015 12:49:58 +0200

camera.app (0.8.0-9.1) unstable; urgency=medium

  * Non-maintainer upload.
  * Build-depend on libgphoto2-dev (Closes: #739348)

 -- Jonathan Wiltshire <jmw@debian.org>  Fri, 08 May 2015 18:49:11 +0100

camera.app (0.8.0-9) unstable; urgency=low

  * Update my email address.
  * Change section to gnustep.
  * Bump standards version to 3.9.1.
  * Bump debhelper version to 7.

 -- Gürkan Sengün <gurkan@phys.ethz.ch>  Tue, 15 Feb 2011 12:36:11 +0100

camera.app (0.8.0-8) unstable; urgency=low

  * GNUstep transition.
    + Updated debian/rules.
    + Updated debian/dirs.
  * Added a desktop file.

 -- Gürkan Sengün <gurkan@linuks.mine.nu>  Wed, 24 Oct 2007 16:38:15 +0200

camera.app (0.8.0-7) unstable; urgency=low

  * Rebuild against latest libgnustep-gui-dev.
  * Bump standards version.

 -- Gürkan Sengün <gurkan@linuks.mine.nu>  Sun, 17 Sep 2006 23:27:40 +0200

camera.app (0.8.0-6) unstable; urgency=low

  * Rebuild against latest libgnustep-gui.
  * Update manual page.
  * Bump standards version.

 -- Gürkan Sengün <gurkan@linuks.mine.nu>  Fri, 20 Jan 2006 10:11:22 +0100
..ect.

---

### Post by joverstreet1 on 2016-10-17
> **joverstreet1 said:**
> Who do I contact about maintaining the contents of this application ?

GNUstep application for digital still cameras - i.e. CAMERA.APP - note NOT CAMERA-APP

Thanks.

Now, how about giving me the SECRET to logging into that website ?

Have no idea how to duplicate a sheep !!!!

Thanks.

---

### Post by mc4man on 2016-10-18
> **joverstreet1 said:**
> 

Have no idea how to duplicate a sheep !!!!

Thanks.
clone

---

### Post by joverstreet1 on 2016-10-19
> **mc4man said:**
> clone

Tried that, doesn't work.

---

### Post by mc4man on 2016-10-19
> **joverstreet1 said:**
> Tried that, doesn't work.

Maybe the whole deal is as dead as the source - 
[https://gna.org/support/?3279](https://gna.org/support/?3279)

---

### Post by mc4man on 2016-10-19
Was bugging me, finally figured out. While not an actual git command it's a 'Git' command
```
Clone
```

---

